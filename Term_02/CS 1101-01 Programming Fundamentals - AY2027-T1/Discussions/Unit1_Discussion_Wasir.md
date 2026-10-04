# Discussion Forum Unit 1: Programming Fundamentals for a Café

**Posted by:** S M Wasir Jayed Rafi
**Course:** CS 1101-01 — Programming Fundamentals (AY2027-T1)

## What Programming Is, and Why It Matters at the Café

Programming is writing instructions that a computer follows the exact same way every time, without guessing at what you meant (Mohbey & Acharya, 2023). That matters for a café that has been tracking orders and menu items by memory or on a notepad. A program can calculate the same order total whether the café is quiet or busy with several customers waiting, and it won't forget a price or skip an item the way a rushed person could. A paper ledger works fine for one order, but it gets harder to manage once the menu grows or the café gets busy.

The café is also a good way to walk through programming's basic pieces. Storing "Cappuccino" and its $5.00 price as *variables* means the price only has to be typed once; if the owner raises drink prices next month, one line changes instead of every receipt being recalculated by hand, the same idea covered in the TeachingCS (2022b) video on how variables store and hold values in a program. An *expression* like `quantity * price` is what actually produces the order total, and the *operator* (`*`) is the symbol doing that work inside the expression. *Control flow* determines what the program does in different situations: an `if` statement can check whether a typed-in item actually exists on the menu before trying to calculate anything, so the program doesn't crash on a typo or a made-up item name.

## Data Types for the Menu

The café owner needs three pieces of information stored for each item, and each one fits a different Python data type (Mohbey & Acharya, 2023). The item name, something like "Cappuccino," is text, so it belongs in a string (`str`): `item_name = "Cappuccino"`. The price needs decimal precision for cents rather than whole numbers, which is what a float gives you: `price = 5.00`. Whether an item is currently available is really just a yes-or-no question, in stock or not, and that maps directly onto Python's Boolean type: `available = True`. An integer can't hold a decimal value at all, so it wouldn't work for a price like $5.50, and a string like `"yes"` for availability would technically work but throws away the direct True/False logic an `if` statement can use right out of the box.

## Arithmetic and Assignment Operators for the Total

Calculating an order's cost is an arithmetic problem: multiply the item's price by how many the customer wants. In Python that's the multiplication operator, `*`, as in `quantity * price`. If a customer orders 2 cappuccinos at $5.00 each, `2 * 5.00` evaluates to `10.00` (Mohbey & Acharya, 2023).

That result still needs somewhere to be stored, and that's the assignment operator's job: `total_cost = quantity * price` stores the calculated value in the variable `total_cost` so it can be reused or printed later. The right side of `=` gets evaluated first, and only then does the result get stored on the left. If the café wanted to add up a total across more than one item in the same order, the shortcut assignment operator `+=` would help: `total_cost += item_price * item_quantity` adds each new item's cost onto whatever `total_cost` already holds, rather than overwriting it (Mohbey & Acharya, 2023).

## The Program

This version of the program handles one menu item and quantity per order, since that's how the café owner described a single customer's purchase:

```python
# Fixed menu with item names as keys and prices as values
menu = {
    "espresso": 2.50,
    "cappuccino": 5.00,
    "latte": 4.50,
    "croissant": 3.50,
    "muffin": 3.00
}

customer_name = input("Customer's name: ")
item = input("Menu item: ").lower()
quantity = int(input("Quantity: "))

if item in menu:
    price = menu[item]
    total_cost = quantity * price  # arithmetic operator calculates the cost
    if quantity == 1:
        item_text = item
    else:
        item_text = item + "s"
    print(f"Customer {customer_name} is buying {quantity} {item_text}. "
          f"Total cost: ${total_cost:.2f}")
else:
    print(f"Sorry, {item} is not on the menu.")
```

Running it for a customer named Nusrat ordering 3 cappuccinos prints: `Customer Nusrat is buying 3 cappuccinos. Total cost: $15.00`. The `input()` calls collect the item and quantity as text, `int()` converts the typed quantity into a number Python can actually multiply with, and the `if item in menu` check keeps the program from crashing if someone types an item that isn't there. A small `if`/`else` adds an "s" when the quantity isn't 1, and the f-string at the end formats the total to two decimal places, similar to how the TeachingCS (2022a) video on Python input and output shows converting raw typed input before using it in a calculation.

A next step, once control flow gets covered more in Unit 2, would be adding the availability check discussed above directly into this program, so a sold-out item gets rejected the same way a misspelled one does.

## Closing Thought

Even a small program like this one, with a five-item menu, one multiplication, and a formatted print statement, can calculate an order's total correctly every time, which is something a paper order pad can't guarantee.

## References

Mohbey, K. K., & Acharya, M. (2023). *Basics of Python programming: A quick guide for beginners*. Bentham Science Publishers.

TeachingCS. (2022a, July 31). *Python for beginners: Inputs & outputs explained* [Video]. YouTube. https://www.youtube.com/watch?v=kvKvYXXuHoo

TeachingCS. (2022b, July 31). *Python for beginners: Variables explained* [Video]. YouTube. https://www.youtube.com/watch?v=SBghUPOWd4w
