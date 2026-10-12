# Discussion Forum Unit 6: Organizing and Managing Data Using Dictionaries and Sets

**Posted by:** S M Wasir Jayed Rafi
**Course:** CS 1101-01 — Programming Fundamentals (AY2027-T1)

## Question 1: Dictionaries for Storing and Retrieving Shipments

A shipment ID points to exactly one shipment, which makes it a natural dictionary key. Mohbey and Acharya (2023) describe a dictionary as a collection that links each key to a value through a mapping relation. Keys can't be duplicated and must be immutable (more precisely, hashable), while values can be any data type and can repeat. Shipment IDs satisfy the requirements for dictionary keys because no two shipments share one, and statuses work as ordinary values since many shipments can be "In Transit" at once. So each ID becomes a key and each status becomes its value.

```python
shipments = {
    "SHP101": "Delivered",
    "SHP102": "In Transit",
    "SHP103": "Pending",
    "SHP104": "In Transit",
    "SHP105": "Delivered",
}

# Direct lookup by key
print("SHP103 status:", shipments["SHP103"])

# get() returns a fallback instead of raising an error for an unknown ID
print("SHP999 status:", shipments.get("SHP999", "Shipment not found"))

# The same data in a list of pairs has to be searched one entry at a time
shipment_list = [("SHP101", "Delivered"), ("SHP102", "In Transit"),
                 ("SHP103", "Pending"), ("SHP104", "In Transit"),
                 ("SHP105", "Delivered")]

def find_status(shipment_id):
    for sid, status in shipment_list:
        if sid == shipment_id:
            return status
    return "Shipment not found"

print("List search for SHP103:", find_status("SHP103"))
```

Output:

```
SHP103 status: Pending
SHP999 status: Shipment not found
List search for SHP103: Pending
```

Retrieving SHP103 takes its ID in square brackets, the key-based access that Mohbey and Acharya (2023) set apart from the index-based access used with lists. Square brackets raise an error when the ID doesn't exist, so for IDs typed in by a clerk I'd use `get()` with a fallback message, as the SHP999 line shows. The last lines hold the same data as a list of pairs, so `find_status()` has to check entry after entry.

That scan is the real cost of using a list, where items are retrieved by index position (Mohbey & Acharya, 2023). Finding a shipment by ID means walking through the entries one by one, and a dictionary avoids that walk. Some other languages call it a hash or associative array (Mohbey & Acharya, 2023). On average, getting a value by key takes constant time, O(1), while checking whether an item is in a list takes time proportional to the list's length, O(n) (Python Software Foundation, n.d.). With five shipments nobody would notice, but with hundreds of thousands the dictionary can answer a "where is my package" query without touching the rest of the data. That source also gives O(n) as the dictionary's worst case, so "faster on average" is the accurate claim.

The prompt also gives each shipment a destination city, which I left out above so the lookup stays easy to follow. A fuller record makes each value a small dictionary holding the city and the status, since one dictionary can be stored inside another (Mohbey & Acharya, 2023).

```python
shipment_records = {
    "SHP101": {"city": "New York", "status": "Delivered"},
    "SHP103": {"city": "Miami", "status": "Pending"},
}

print(shipment_records["SHP103"]["status"])
print(shipment_records["SHP103"]["city"])
```

Output:

```
Pending
Miami
```

One ID key now returns both fields.

## Question 2: Dictionary Methods for Managing and Reporting

The same square-bracket syntax does two jobs. Assigning to a key that exists replaces its value, and assigning to a new key adds an entry (Mohbey & Acharya, 2023), so SHP102 becomes "Delivered" and SHP106 joins the system with one line each. A mistyped ID wouldn't raise an error here, though. It would quietly create a new shipment, so a real system should check first. To remove a completed shipment I used `pop()` instead of `del`. According to Mohbey and Acharya (2023), `del` throws an exception when the key is missing, whereas `pop()` can return a default value instead of failing, but only if you supply one, since `pop("SHP999")` alone raises a `KeyError` too. It also returns the value it removed, which matters here because the final status of SHP101 comes back in the same step, as the first output line shows.

```python
shipments = {
    "SHP101": "Delivered",
    "SHP102": "In Transit",
    "SHP103": "Pending",
    "SHP104": "In Transit",
    "SHP105": "Delivered",
}

shipments["SHP102"] = "Delivered"      # update an existing status
shipments["SHP106"] = "Pending"        # add a new shipment
last_status = shipments.pop("SHP101")  # remove a completed shipment
print("Removed SHP101, last status was:", last_status)
print("pop() on a missing ID with a default:", shipments.pop("SHP999", "not on file"))
print()

print("IDs:", list(shipments.keys()))
print("Statuses:", list(shipments.values()))
print("Pending shipments:", list(shipments.values()).count("Pending"))
print()

for shipment_id, status in shipments.items():
    print(f"{shipment_id} -> {status}")
```

Output:

```
Removed SHP101, last status was: Delivered
pop() on a missing ID with a default: not on file

IDs: ['SHP102', 'SHP103', 'SHP104', 'SHP105', 'SHP106']
Statuses: ['Delivered', 'Pending', 'In Transit', 'Delivered', 'Pending']
Pending shipments: 2

SHP102 -> Delivered
SHP103 -> Pending
SHP104 -> In Transit
SHP105 -> Delivered
SHP106 -> Pending
```

For summaries, `keys()` returns the shipment IDs, `values()` returns the statuses, and `items()` returns each pair together. All three produce iterable view objects (Mohbey & Acharya, 2023), so I wrapped the first two in `list()` to make them print cleanly. With the statuses in a list, `.count("Pending")` gives the number of waiting shipments in one line, useful for a manager's morning report.

These methods improve daily operations in three ways. For accuracy, `items()` keeps every ID attached to its own status, so a report can't pair SHP102 with SHP103's status the way two parallel lists could if only one got edited. Because each ID is one key, a shipment holds one current status at a time, and updating it replaces the old value instead of adding a second entry. `pop()` also hands back what it removed, so nothing disappears unnoticed. Readability comes from the method names, so `for shipment_id, status in shipments.items()` reads almost like the sentence it replaces. Efficiency is the last gain: getting, setting, and deleting by key are O(1) on average (Python Software Foundation, n.d.), and a report loop makes one pass over the data instead of searching again for each shipment.

## Question 3: Sets for Unique Delivery Cities

A city is either on a region's delivery list or it isn't, which is exactly the yes-or-no question a set answers. A set, according to Wang (2022), groups data under one name without a fixed size or index numbers, and its contents come out in no particular order. I sorted each result before printing it because a raw set could show the cities in a different order on another run.

```python
north = {"New York", "Dallas", "Miami"}
south = {"Miami", "Atlanta", "Dallas"}

all_cities = north.union(south)
shared = north.intersection(south)
north_only = north.difference(south)
south_only = south.difference(north)

print("Union:", sorted(all_cities))
print("Intersection:", sorted(shared))
print("North only:", sorted(north_only))
print("South only:", sorted(south_only))
print()

# Duplicates in a raw delivery log disappear once it becomes a set
delivery_log = ["Miami", "Dallas", "Miami", "Atlanta", "Dallas", "Miami"]
unique_cities = set(delivery_log)
print(len(delivery_log), "log entries,", len(unique_cities), "unique cities")
print("Is Atlanta served?", "Atlanta" in unique_cities)
```

Output:

```
Union: ['Atlanta', 'Dallas', 'Miami', 'New York']
Intersection: ['Dallas', 'Miami']
North only: ['New York']
South only: ['Atlanta']

6 log entries, 3 unique cities
Is Atlanta served? True
```

Each operation answers a different business question. The union merges both regions into one company-wide list, making it useful for counting service locations. Miami and Dallas appear in both regions but only once in the result, which matches Wang's (2022) note that a union doesn't store duplicate data twice. The intersection returns Dallas and Miami, the cities both regions serve, so it shows where the two regions overlap and may be duplicating effort. The difference returns what remains in one set after the common cities are removed. The order of the sets matters, as Wang (2022) stresses, because `difference()` keeps what is in the first set but not the second, so I ran it both ways: `north.difference(south)` gives New York, while `south.difference(north)` gives Atlanta. Those cities have only one region behind them, so a closed hub there would leave them with no backup.

Duplicates are where sets earn their place in logistics. A delivery log records a city every time a package goes there, so the sample log above has six entries but only three real cities. Counting the raw list would report six locations instead of three, which throws off any report built on that number. Because a set automatically excludes duplicate data (Wang, 2022), everything left in it is guaranteed to be unique. Membership checks are cleaner too. A simple `in` test tells you whether a value is stored, where older languages often had to examine an array element by element (Wang, 2022). Python's complexity tables rate that test O(1) on average for a set versus O(n) for a list (Python Software Foundation, n.d.).

Sets do have a limit, though. Wang (2022) points out that there isn't always an easy way to get one individual item back out, and that sets work best when data is treated as a group. They're unordered, so indexing a set raises a `TypeError`, and `pop()` removes an arbitrary element rather than one I choose. So the prototype would use both structures: a dictionary for per-shipment records that must be looked up by ID, and sets for questions about whole groups of cities.

## References

Mohbey, K. K., & Acharya, M. (2023). *Basics of python programming : A quick guide for beginners*. Bentham Science Publishers.

Python Software Foundation. (n.d.). *TimeComplexity*. Python Wiki. https://wiki.python.org/moin/TimeComplexity

Wang, W. (2022). *Beginning programming all-in-one for dummies*. John Wiley & Sons, Incorporated.
