# Design Documentation for Blinkit

## Table of Contents
### 1. Introduction  
- 1.1 Purpose  
- 1.2 Scope  
- 1.3 Overview  
- 1.4 Reference Material  
- 1.5 Definitions and Acronyms  

### 2. System Overview  

### 3. System Architecture  
- 3.1 Architectural Design  
- 3.2 Decomposition Description  
- 3.3 Design Rationale  

### 4. Data Design  
- 4.1 Data Description  
- 4.2 Data Dictionary  

### 5. Component Design  
- 5.1 Order Management System  

### 6. Human Interface Design  
- 6.1 Overview of User Interface  
- 6.2 Screen Images  
- 6.3 Screen Objects and Actions  

### 7. Requirements Matrix  

---

## 1. Introduction  

### 1.1 Purpose  
This document outlines the software design for Blinkit, a grocery delivery application. The purpose of this document is to serve as a blueprint for developers and stakeholders to understand the system's architecture, data flow, and user interactions, ensuring seamless implementation and maintenance.

### 1.2 Scope  
Blinkit aims to offer a fast, efficient, and user-friendly platform for ordering groceries. Key features include:  
- **Fast Delivery**: Deliver groceries within minutes.  
- **User-Friendly Interface**: Intuitive design for all user demographics.  
- **Order Tracking**: Real-time updates on delivery status.  
- **Diverse Catalog**: Wide variety of grocery items categorized efficiently.  
- **Secure Payments**: Integration with multiple payment gateways.  

### 1.3 Overview  
This document includes:  
- **System Overview**: High-level functional description.  
- **System Architecture**: Modular breakdown of the app.  
- **Data Design**: Details of data storage and management.  
- **Component Design**: Key functionalities explained.  
- **Human Interface Design**: Screens and interactions.  
- **Requirements Matrix**: Mapping functionalities to components.

### 1.4 Reference Material  
- Analysis of grocery delivery app architectures.  
- Studies on UI/UX in fast-paced delivery services.  
- Feedback from users of existing Blinkit services.  

### 1.5 Definitions and Acronyms  
| Term            | Definition                                            |  
|------------------|------------------------------------------------------|  
| UI              | User Interface                                       |  
| API             | Application Programming Interface                    |  
| OMS             | Order Management System                              |  
| ETA             | Estimated Time of Arrival                            |  

---

## 2. System Overview  
The Blinkit application is a platform that connects users to local grocery stores. Users can browse items, add them to a cart, and place orders, which are then processed and delivered in real-time.

---

## 3. System Architecture  

### 3.1 Architectural Design  
The architecture is modular and scalable, ensuring efficiency in handling concurrent users. Key layers include:  
- **User Interface Layer**: Manages interactions like browsing and checkout.  
- **Backend Services**: Processes orders, updates inventory, and handles payments.  
- **Delivery Management System**: Tracks orders and assigns delivery personnel.  
- **Database Layer**: Stores user, product, and order data.  

### 3.2 Decomposition Description  
#### UI Module:  
- **Login & Registration**  
- **Home Page & Search**  
- **Cart & Checkout**  

#### Backend Module:  
- **Order Processing**  
- **Inventory Management**  
- **Payment Gateway Integration**  

### 3.3 Design Rationale  
The modular architecture supports independent updates, like enhancing the payment gateway without impacting other components.  

---

## 4. Data Design  

### 4.1 Data Description  
Blinkit organizes data into three categories:  
- **User Data**: Account details, preferences, and order history.  
- **Product Data**: Inventory details, categories, and prices.  
- **Order Data**: Status, ETA, and payment details.  

### 4.2 Data Dictionary  
| Field Name      | Data Type   | Description                      |  
|------------------|------------|----------------------------------|  
| user_id         | Integer    | Unique user identifier.          |  
| product_id      | Integer    | Unique product identifier.       |  
| order_status    | String     | Current status of the order.     |  
| payment_method  | String     | Mode of payment used.            |  

---

## 5. Component Design  

### 5.1 Order Management System  
- **Functionality**: Handles end-to-end order processing.  
- **Algorithm**:  
  1. Accept user order.  
  2. Validate inventory availability.  
  3. Confirm payment.  
  4. Assign delivery agent.  
  5. Update order status in real-time.
  ![image](https://github.com/user-attachments/assets/e7f8fd6d-7587-4881-b36c-814cc10199b4)


---

## 6. Human Interface Design  

### 6.1 Overview of User Interface  
The app's interface emphasizes ease of navigation and quick access to key functionalities like searching products, viewing cart, and tracking orders.

### 6.2 Screen Images  
1. **Login Screen**: Allows users to log in or register.  
2. **Home Screen**: Displays product categories and search bar.  
3. **Cart Screen**: Lists selected items and calculates total.  
4. **Order Tracking Screen**: Shows order status and ETA.  

### 6.3 Screen Objects and Actions 

## Login Page

| **Field**        | **Description**                                      | **Example**         |
|------------------|------------------------------------------------------|---------------------|
| Username         | Field for the user to input their username.         | "john_doe"          |
| Password         | Field for the user to input their password.         | "********"          |
| Forgot Password  | Link to reset the password if forgotten.            | "Forgot Password?"  |
| Login Button     | Button to submit login details.                      | "Log In"            |
| Sign Up Link     | Link to redirect users to the registration page.    | "Sign Up"           |

![LoginPage](https://github.com/user-attachments/assets/471d9dd4-8765-4a72-b911-e3a91d52c25e)


## Dashboard

| **Section**      | **Description**                                      | **Example**               |
|------------------|------------------------------------------------------|---------------------------|
| User Information | Displays the user's name and profile picture.       | "John Doe, 25XP"          |
| Progress Tracker | Shows the user's learning progress (percentage).    | "80% completed"           |
| Daily Goal       | Displays the user's daily learning target.          | "Complete 3 lessons"      |
| Streak Status    | Shows the user's current streak.                    | "Streak: 5 days"          |
| Leaderboard      | Displays the user's ranking based on points.        | "Rank: 3rd"               |

![Dashboard](https://github.com/user-attachments/assets/c046d6a5-5b76-414e-8b0f-b6076383652b)


## MyCart

| **Item**         | **Description**                                      | **Example**               |
|------------------|------------------------------------------------------|---------------------------|
| Product Name     | Name of the product in the cart.                    | "Wireless Mouse"          |
| Quantity         | Number of units of the product.                     | "1"                       |
| Price            | Price of the product.                               | "$25"                     |
| Remove Button    | Button to remove the product from the cart.         | "Remove"                  |
| Checkout Button  | Button to proceed to checkout.                      | "Proceed to Checkout"     |

![Mycart2](https://github.com/user-attachments/assets/d1b7140d-46a4-4df7-8c8a-b1f93e3cc004)

## Order History
![order again](https://github.com/user-attachments/assets/6fc78f9d-649d-4766-9246-166a2da8b250)




---

## Requirements Matrix

| **Requirement**                         | **Component**            | **Description**                                               | **Priority** |
|-----------------------------------------|--------------------------|---------------------------------------------------------------|--------------|
| User Login                              | Login Page               | Allows the user to log into their Blinkit account.            | High         |
| User Registration                       | Registration Page        | Allows new users to create a Blinkit account.                 | High         |
| View Products                           | Product Page             | Displays a list of available products with details.           | High         |
| Product Search                          | Search Bar               | Allows users to search for products by name or category.      | High         |
| Cart Management                         | MyCart                   | Allows users to view and manage items added to the cart.      | High         |
| Order Placement                         | Order Management System  | Handles order creation, payment, and confirmation.            | High         |
| Delivery Tracking                       | Delivery Tracker         | Allows users to track the status of their orders in real-time. | High         |
| User Profile                            | Profile Page             | Displays user's personal information, order history, etc.     | Medium       |
| Notifications                           | Notification System      | Sends updates to users regarding order status and promotions. | Medium       |
| Payment Processing                      | Payment Gateway          | Handles payment processing for orders.                       | High         |
| Order History                          | Order History Page       | Displays past orders and details of previous transactions.    | Medium       |
| User Feedback                          | Review and Ratings       | Allows users to rate and review products.                     | Low          |
 

