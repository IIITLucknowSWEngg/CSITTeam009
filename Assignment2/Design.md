# Design Documentation for Blinkit

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

## 7. Database Design

### 7.1 Overview
The Blinkit platform utilizes a combination of relational, NoSQL, and in-memory databases to ensure scalability, high performance, and flexibility. The following databases are used:

- **PostgreSQL**: Relational database for structured data like user information, orders, and payments.
- **MongoDB**: NoSQL database for dynamic product catalogs, user preferences, and logs.
- **Redis**: In-memory database for caching user sessions, product search results, and real-time tracking data.
- **Elasticsearch**: Search engine database for optimized product search functionality.

### 7.2 Database Systems

#### **PostgreSQL** (Relational Database)
**Reason**: Stores structured data that requires ACID compliance, such as user details, product inventory, order information, and payment transactions.

##### Key Tables:
- **Users**: Stores user details such as name, email, and address.
- **Products**: Stores product details including name, category, price, and stock quantity.
- **Orders**: Manages orders, including status, ETA, and payment data.
- **Payments**: Stores payment transaction data for each order.

##### Example Schema:
| Column Name       | Data Type   | Description                             |
|-------------------|-------------|-----------------------------------------|
| user_id           | INTEGER     | Unique identifier for the user (PK)     |
| name              | VARCHAR(100)| User's name                             |
| email             | VARCHAR(100)| User's email address                    |
| password_hash     | VARCHAR(255)| Hashed password for security            |

#### **MongoDB** (NoSQL Database)
**Reason**: Used for storing flexible, semi-structured data such as product catalogs, user preferences, and activity logs.

##### Key Collections:
- **User Preferences**: Stores personalized user data like favorite products and recent searches.
- **Product Catalog**: Stores dynamic product information including special offers and promotional details.
- **Activity Logs**: Logs user interactions such as product searches, cart additions, and order placements.

#### **Redis** (In-memory Database)
**Reason**: Caches frequently accessed data to enhance performance, such as real-time order tracking and session management.

##### Cache Use Cases:
- **Product Search**: Caches the results of product searches to improve response times.
- **User Sessions**: Stores user session data, such as cart items and preferences, for faster access.
- **Order Tracking**: Caches live tracking data for orders to ensure users get timely updates.

#### **Elasticsearch** (Search Engine Database)
**Reason**: Provides fast, efficient full-text search capabilities for the product catalog.

##### Key Indexes:
- **Product Index**: Indexes product names, categories, and attributes for search optimization.
- **User Search History**: Indexes user search history to offer personalized search results.

### 7.3 Data Flow and Interaction Between Databases

1. **User Places an Order**:
    - **PostgreSQL** manages user authentication, order creation, and payment.
    - **MongoDB** stores user preferences and shopping history for future recommendations.
    - **Redis** caches session data and real-time order tracking.
    - **Elasticsearch** provides quick and efficient search results for products.
    - **Redis** ensures quick access to frequently accessed data like product catalogs and real-time order status.

### 7.4 Backup and Data Redundancy
- **PostgreSQL** and **MongoDB** will have daily backups for data redundancy.
- **Redis** uses an eviction strategy to manage memory efficiently, with important data being backed up periodically.
- **Elasticsearch** indexes are replicated across multiple nodes for fault tolerance.

---




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
 

