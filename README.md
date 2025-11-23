# vityarthi
Simple Food Ordering System

Overview

This project is a beginner-friendly console-based food ordering application suitable for small restaurants and cafes. It lets users browse the menu, add items to their cart, checkout orders, print sales reports, and export order records to CSV. An admin can update menu items, making it ideal for learning basic Python file handling, menus, and simple reporting.

Features
View restaurant menu
Add food items to a customer cart
Display cart with total prices
Checkout and order placement
Digital order history with timestamps
Admin functions: add/remove menu items
Daily total sales report
Export order history in CSV format
Technologies/Tools Used
Python 3.x for all back-end logic
JSON files for menu and order storage
CSV module for order exports
Pathlib for file/directory handling (cross-platform)
No external dependencies

Steps to Install & Run
Install Python
Ensure Python 3.x is installed. Download from python.org if missing.

Clone or Download the Repository
Place all .py files in a folder. The script auto-creates its data subdirectory.

Run the Application
Open a terminal/cmd.
Navigate to the project directory.


Instructions For Testing
On startup, default menu items ("Burger", "Pizza", "Pasta") are created.

Use the numbered menu to perform actions:

1: Browse menu

2: Add item to cart (by ID)

3: View current cart

4: Checkout and place order (cart clears)

5: View past orders

6: Daily sales report (today's total)

7: Admin panel: add new menu items

8: Admin panel: remove menu items by ID

9: Export all orders to orders_export.csv

10: Exit

Test all features by adding items, ordering, and using admin options.
For admins, confirm changes via options 7 (add) and 8 (remove).
Check the data folder for menu.json and orders.json.
After exporting, open orders_export.csv in Excel or any spreadsheet viewer.
