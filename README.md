# Assignment-1---
Description: Delivery Management System
# Enum for Account Status
class AccountStatus:
    ACTIVE = "active"
    INACTIVE = "inactive"
    LOCKED = "locked"


# Customer Class
class Customer:
    def __init__(self, username, password, account_status):
        # Initializing attributes
        self.username = username  # Public attribute
        self.__password = password  # Private attribute
        self.account_status = account_status  # Public attribute

    # Getter for username
    def get_username(self):
        return self.username

    # Setter for username
    def set_username(self, username):
        self.username = username

    # Login method
    def login(self):
        if self.account_status == AccountStatus.ACTIVE:
            return f"Customer {self.username} logged in successfully."
        else:
            return "Account is inactive. Please contact support."

    # String representation
    def __str__(self):
        return f"Customer(username={self.username}, account_status={self.account_status})"


# Order Class
class Order:
    def __init__(self, order_id, items, total_amount, status):
        self.order_id = order_id  # Public attribute
        self.items = items  # Public attribute
        self.__total_amount = total_amount  # Private attribute
        self.status = status  # Public attribute

    # Getter for order_id
    def get_order_id(self):
        return self.order_id

    # Setter for order_id
    def set_order_id(self, order_id):
        self.order_id = order_id

    # Place order method
    def place_order(self):
        self.status = "placed"
        return f"Order {self.order_id} has been placed."

    # Update order status
    def update_status(self, new_status):
        self.status = new_status
        return f"Order {self.order_id} status updated to {self.status}."

    # String representation
    def __str__(self):
        return f"Order(order_id={self.order_id}, items={self.items}, total_amount={self.__total_amount}, status={self.status})"


# Payment Class
class Payment:
    def __init__(self, payment_id, payment_method, amount, status):
        self.payment_id = payment_id  # Public attribute
        self.payment_method = payment_method  # Public attribute
        self.__amount = amount  # Private attribute
        self.status = status  # Public attribute

    # Process payment method
    def process_payment(self):
        if self.status == "success":
            return f"Payment {self.payment_id} processed successfully."
        else:
            return "Payment failed. Please try again."

    # Refund method
    def refund(self):
        if self.status == "success":
            self.status = "refunded"
            return f"Payment {self.payment_id} has been refunded."
        else:
            return "Refund cannot be processed."

    # String representation
    def __str__(self):
        return f"Payment(payment_id={self.payment_id}, payment_method={self.payment_method}, amount={self.__amount}, status={self.status})"


# Delivery Class
class Delivery:
    def __init__(self, delivery_id, delivery_status, estimated_time):
        self.delivery_id = delivery_id  # Public attribute
        self.delivery_status = delivery_status  # Public attribute
        self.__estimated_time = estimated_time  # Private attribute

    # Track delivery method
    def track_delivery(self):
        return f"Delivery {self.delivery_id} is {self.delivery_status}. Estimated time: {self.__estimated_time}."

    # Assign agent method
    def assign_agent(self, agent_name):
        return f"Delivery {self.delivery_id} has been assigned to {agent_name}."

    # String representation
    def __str__(self):
        return f"Delivery(delivery_id={self.delivery_id}, delivery_status={self.delivery_status}, estimated_time={self.__estimated_time})"


# Test the Classes

# Create objects
customer1 = Customer("Ahmed Ali", "password123", AccountStatus.ACTIVE)
order1 = Order("ORD12545", ["item1", "item2"], 250.00, "placed")
payment1 = Payment("PAY12345", "credit_card", 250.00, "success")
delivery1 = Delivery("DEL12345", "out_for_delivery", "2:00 PM")

# Print the object details using __str__ method
print(customer1)
print(order1.place_order())
print(payment1.process_payment())
print(delivery1.track_delivery())

# Update and print updated objects
order1.update_status("shipped")
print(order1)

# Print individual method outputs
print(customer1.login())
print(payment1.refund())
print(delivery1.assign_agent("Agent A"))
