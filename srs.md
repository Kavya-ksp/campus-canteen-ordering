# Software Requirements Specification (SRS)
## Campus Canteen Ordering System

**Version:** 1.0  
**Status:** Draft

---

## 1. Introduction

### 1.1 Purpose
The purpose of the Campus Canteen Ordering System is to allow students and staff to view the canteen menu, order food online, and track their order status. The system aims to reduce queues, save time, and improve the efficiency of canteen operations.

### 1.2 Scope
The system will provide an online platform for campus users to:
- View available food items and their prices.
- Add food items to a cart.
- Place and cancel orders, subject to order status.
- Track order progress.
- View previous orders.

Canteen staff will be able to manage menu items, update availability, and process incoming orders.

### 1.3 Intended Audience
- Students and staff who use the canteen.
- Canteen administrators and employees.
- Developers and testers working on the project.
- Faculty members evaluating the project.

### 1.4 Definitions and Abbreviations
- **SRS:** Software Requirements Specification.
- **UI:** User Interface.
- **User:** A student or staff member using the system.
- **Admin:** A person authorized to manage the menu and orders.
- **Cart:** A temporary list of food items selected for purchase.

---

## 2. Overall Description

### 2.1 Product Perspective
The Campus Canteen Ordering System is a web-based application that connects campus users with canteen staff. It provides a centralized platform for browsing the menu and managing food orders.

### 2.2 Product Functions
The main functions of the system are:
1. User registration and login.
2. Displaying the food menu.
3. Searching and filtering food items.
4. Adding and removing items from the cart.
5. Placing and cancelling orders.
6. Displaying order status.
7. Managing food items and availability.
8. Viewing order history.
9. Managing and updating incoming orders.

### 2.3 User Classes

**Student/Staff**
- Register and log in.
- Browse food items.
- Place orders and view order status.
- View previous orders.

**Canteen Staff**
- View incoming orders.
- Accept and prepare orders.
- Update order status.
- Mark food items as unavailable.

**Administrator**
- Add, edit, or remove food items.
- Manage user access where authorized.
- Monitor orders and menu availability.

### 2.4 Operating Environment
- Operating System: Windows, Linux, or macOS.
- Client: Modern web browser such as Chrome or Firefox.
- Frontend: HTML, CSS, JavaScript, or a suitable frontend framework.
- Backend: Python with Flask or FastAPI, or another suitable backend.
- Database: MySQL, PostgreSQL, or SQLite.

### 2.5 Assumptions and Dependencies
- Users have access to a device with an internet or campus network connection.
- Canteen staff regularly update food availability.
- Users provide valid registration information.
- The canteen is responsible for preparing and handing over orders.
- Online payment is optional and depends on the implementation.

---

## 3. Functional Requirements

### FR-01: User Registration
The system shall allow new users to register using required details such as name, email address, and password.

### FR-02: User Login
The system shall authenticate registered users before allowing access to account-specific features.

### FR-03: View Menu
The system shall display available food items with their names, descriptions, prices, and availability.

### FR-04: Search Food Items
The system shall allow users to search for food items by name or category.

### FR-05: Manage Cart
The system shall allow users to add items to the cart, change quantities, and remove items before checkout.

### FR-06: Place Order
The system shall validate the cart and create an order when the user confirms checkout.

### FR-07: Order Tracking
The system shall display the current status of an order. Possible statuses include:
- Placed
- Accepted
- Preparing
- Ready for Pickup
- Completed
- Cancelled

### FR-08: Cancel Order
The system shall allow users to cancel an order only when its status and the canteen's cancellation policy permit it.

### FR-09: Order History
The system shall allow users to view their previous orders and order details.

### FR-10: Menu Management
The system shall allow authorized staff to add, update, and remove food items and change their availability.

### FR-11: Order Management
The system shall allow canteen staff to view incoming orders and update their status.

### FR-12: Access Control
The system shall restrict administrative and staff functions to authorized accounts.

---

## 4. Non-Functional Requirements

### 4.1 Performance
- The menu should load within 3 seconds under normal operating conditions.
- The system should process a normal order submission within 5 seconds, excluding external payment delays.

### 4.2 Security
- Passwords shall be stored using secure password hashing.
- The system shall validate user inputs.
- Users shall only be able to access their own order history.
- Administrative features shall require appropriate authorization.

### 4.3 Usability
- The interface shall be simple and easy to navigate.
- Menu items, prices, and order statuses shall be clearly displayed.
- The application shall support common desktop and mobile screen sizes.

### 4.4 Reliability
- The system shall prevent orders from being created with invalid quantities or unavailable items.
- Order information shall be stored consistently.
- Errors shall be displayed with understandable messages.

### 4.5
