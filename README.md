# vityarthi
**Simple Food Ordering System**

**Overview**

This is a simple, console-based food ordering application designed for small restaurants and cafes. Users can view the menu, add food items to a cart, checkout to place orders, and admins can manage the menu and view sales reports. It demonstrates core Python programming concepts including file handling, user input, and basic data persistence.

**Features**

- View the current food menu with item names and prices
- Add selected items to a shopping cart with quantities
- View cart contents and total bill amount
- Checkout to place orders with customer details
- Admin functions to add or remove menu items
- View all past orders along with order timestamps
- Generate daily sales report for the current day
- Export order history as a CSV file for external review

**Technologies Used**

- Python 3.x (No external libraries required)
- JSON files for menu and order data persistence
- CSV files for exporting order history
- Pathlib module for cross-platform file handling

**Installation**

- Ensure Python 3.x is installed on your system. Download it from [python.org](https://python.org/) if necessary.
- Clone or download the project files into a folder on your local machine.
- There is no additional setup - the program creates necessary data folders and files on first run.

**How to Run**

- Open a terminal or command prompt.
- Navigate to the folder containing the project's Python script file (e.g., food_ordering_system.py).
- Run the script using:

text

python food_ordering_system.py

- Follow the on-screen menu to interact with the system.

**Usage Instructions**

- **View Menu:** Select option 1 to see all available food items.
- **Add to Cart:** Select option 2, then enter the item ID and quantity to add to your shopping cart.
- **View Cart:** Use option 3 to see current items in your cart along with the total price.
- **Checkout:** Choose option 4, enter your name, and place your order. The cart will clear after successful checkout.
- **View Orders:** Option 5 displays all previous orders with timestamps and totals.
- **Daily Sales:** Option 6 shows today's total sales amount.
- **Admin Add Item:** Option 7 allows adding new menu items by providing ID, name, and price.
- **Admin Remove Item:** Option 8 removes a menu item using its ID.
- **Export Orders CSV:** Option 9 exports all orders to a CSV file named orders_export.csv in the project directory.
- **Exit:** Option 10 ends the program.

**Contributing**

This project is intended for beginners and educational purposes. Contributions and improvements are welcome! Please fork the repository and submit pull requests.

**License**

This project is open source and free to use under the MIT License.
