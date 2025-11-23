
"""
Simple Food Ordering System (Beginner-Friendly Version)

This program lets users:
- View menu
- Add food items to a cart
- View cart
- Checkout and place orders
- Admin can add/remove menu items
- Daily sales report
- Export order history to CSV
"""

import json
from pathlib import Path
from datetime import datetime
import csv


DATA = Path('data')
MENU_FILE = DATA / 'menu.json'
ORDERS_FILE = DATA / 'orders.json'

# Make sure the "data" folder exists
DATA.mkdir(exist_ok=True)

# Create default menu if menu.json is missing
if not MENU_FILE.exists():
    default_menu = [
        {"id": "M1", "name": "Burger", "price": 80},
        {"id": "M2", "name": "Pizza", "price": 250},
        {"id": "M3", "name": "Pasta", "price": 150}
    ]
    MENU_FILE.write_text(json.dumps(default_menu, indent=2), encoding='utf-8')

# Create empty orders file if missing
if not ORDERS_FILE.exists():
    ORDERS_FILE.write_text('[]', encoding='utf-8')




def load_json(path):
    """Load a JSON file safely. If something goes wrong, return an empty list."""
    try:
        return json.loads(path.read_text(encoding='utf-8'))
    except:
        return []


def save_json(path, data):
    """Save Python lists/dictionaries to JSON file in a pretty format."""
    path.write_text(json.dumps(data, indent=2), encoding='utf-8')




def view_menu():
    """Show all items in the menu."""
    menu = load_json(MENU_FILE)
    print("\n--- MENU ---")
    for item in menu:
        print(f"{item['id']}: {item['name']} - Rs {item['price']}")
    return menu


def find_menu_item(item_id):
    """Find a menu item by its ID, ignoring case."""
    menu = load_json(MENU_FILE)
    for item in menu:
        if item['id'].lower() == item_id.lower():
            return item
    return None



def add_to_cart(cart, item_id, qty=1):
    """Add an item to the user's cart."""
    item = find_menu_item(item_id)

    if not item:
        print("Item not found!")
        return

    cart.append({
        "id": item["id"],
        "name": item["name"],
        "price": item["price"],
        "qty": qty
    })
    print("Item added to cart!")


def view_cart(cart):
    """Display cart contents and calculate total bill."""
    if not cart:
        print("Your cart is empty.")
        return

    print("\n--- YOUR CART ---")
    total = 0

    for idx, item in enumerate(cart, start=1):
        line_amount = item["price"] * item["qty"]
        total += line_amount
        print(f"{idx}. {item['name']} x{item['qty']} = Rs {line_amount}")

    print("Total = Rs", total)
    return total




def checkout(cart, customer_name):
    """Place an order and save it permanently."""
    if not cart:
        print("Cart is empty!")
        return

    orders = load_json(ORDERS_FILE)

    # Create unique order ID using current time
    order_id = "O" + datetime.now().strftime("%Y%m%d%H%M%S")

    # Calculate total amount
    total = sum(item["price"] * item["qty"] for item in cart)

    # Order structure
    order = {
        "order_id": order_id,
        "customer": customer_name,
        "items": cart.copy(),
        "total": total,
        "time": datetime.now().isoformat()
    }

    # Save order to file
    orders.append(order)
    save_json(ORDERS_FILE, orders)

    print(f"Order placed! ID: {order_id} | Total: Rs {total}")

    # Clear user's cart
    cart.clear()



def admin_add_item():
    """Admin can manually add new menu items."""
    menu = load_json(MENU_FILE)

    new_id = input("Enter new item ID (e.g., M4): ").strip()
    name = input("Enter item name: ").strip()

    try:
        price = float(input("Enter price: ").strip())
    except:
        print("Invalid price!")
        return

    menu.append({"id": new_id, "name": name, "price": price})
    save_json(MENU_FILE, menu)

    print("Item added successfully!")


def admin_remove_item():
    """Admin can remove an item by ID."""
    menu = load_json(MENU_FILE)
    item_id = input("Enter item ID to remove: ").strip()

    new_menu = [item for item in menu if item["id"].lower() != item_id.lower()]
    save_json(MENU_FILE, new_menu)

    print("Item removed (if it existed).")


def view_orders():
    """Show all previously placed orders."""
    orders = load_json(ORDERS_FILE)

    if not orders:
        print("No orders found.")
        return

    for order in orders:
        print(f"{order['order_id']} | {order['customer']} | Rs {order['total']} | {order['time']}")


def daily_sales():
    """Show today's total sales."""
    today = datetime.now().date().isoformat()
    orders = load_json(ORDERS_FILE)

    total_today = sum(order["total"] for order in orders if order["time"].startswith(today))
    print("Today's sales: Rs", total_today)


def export_orders_csv(filename="orders_export.csv"):
    """Export all orders into a CSV file."""
    orders = load_json(ORDERS_FILE)
    columns = ["order_id", "customer", "total", "time"]

    try:
        with open(filename, "w", newline="", encoding="utf-8") as file:
            writer = csv.DictWriter(file, fieldnames=columns)
            writer.writeheader()

            for order in orders:
                writer.writerow({col: order.get(col, "") for col in columns})

        print("Orders exported to", filename)
    except Exception as e:
        print("Failed to export CSV:", e)




def menu_text():
    """Return the menu text shown to the user."""
    return """
Food Ordering System
1. View menu
2. Add to cart
3. View cart
4. Checkout
5. View orders
6. Daily sales
7. Admin add item
8. Admin remove item
9. Export orders CSV
10. Exit
Choose (1-10): """


def main():
    cart = []

    while True:
        choice = input(menu_text()).strip()

        if choice == "1":
            view_menu()
        elif choice == "2":
            item_id = input("Enter item ID: ").strip()
            try:
                qty = int(input("Quantity: ").strip() or "1")
            except:
                qty = 1
            add_to_cart(cart, item_id, qty)
        elif choice == "3":
            view_cart(cart)
        elif choice == "4":
            name = input("Customer name: ").strip()
            checkout(cart, name)
        elif choice == "5":
            view_orders()
        elif choice == "6":
            daily_sales()
        elif choice == "7":
            admin_add_item()
        elif choice == "8":
            admin_remove_item()
        elif choice == "9":
            export_orders_csv()
        elif choice == "10":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")


# Entry point
if __name__ == "__main__":
    main()
