# Test Plan for Blinkit 

## 1. Introduction
The Blinkit Clone is a platform connecting users with grocery stores and delivery services.  
This document outlines the testing methodology to ensure quality and performance.

---

## 2. Scope

### Components to Test:
- *Customer Module*: Registration, login, profile management, product search, and favorites.
- *Store Module*: Inventory display, reviews, and ratings.
- *Order Management Module*: Placement, modification, and payment processing.
- *Delivery Module*: Assign orders and track deliveries.
- *Admin Module*: Manage stores, inventory, and view reports.
- *Third-Party Integrations*: Google Maps API, notification services, and payment gateways.

---

## 3. Modules Overview

### 1. Customer Module
*Features:*
- Registration/Login: Account creation and secure login.
- Profile Management: Update and view customer details.
- Search: Find products or stores.
- Favorites: Save favorite stores and products.

### 2. Store Module
*Features:*
- Inventory Display: View product details, descriptions, and prices.
- Reviews and Ratings: Submit and view store feedback.
- Store Info: Address, hours of operation, and contact details.

### 3. Order Management Module
*Features:*
- Cart: Add, edit, or remove items.
- Order Placement: Finalize and submit orders.
- Payment Gateway: Secure payments via multiple modes.
- Order History: View past orders and receipts.

### 4. Delivery Module
*Features:*
- Assign Driver: Allocate orders to delivery personnel.
- Real-Time Tracking: Track delivery progress.
- Delivery Confirmation: Mark orders as delivered.

### 5. Admin Module
*Features:*
- Store Management: Add/update store details and inventory.
- Order Monitoring: Track and manage active orders.
- Reports: Analytics on orders, users, and revenue.

---

## 4. Objectives
- Validate functionality across all modules.
- Ensure data security, especially in payment processes.
- Test performance under high user traffic.
- Verify customer experience on different devices.

---

## 5. Testing Strategy

### Types of Testing:
- *Unit Testing*: Individual components like login or inventory display.
- *Integration Testing*: Interaction between modules, e.g., customer orders with stores.
- *System Testing*: Full system compliance with requirements.
- *Performance Testing*: Load testing with high traffic (e.g., 10,000 users).
- *Security Testing*: Vulnerability checks like SQL injection and authentication.
- *Usability Testing*: Ensure seamless customer experience.

---

## 6. Test Environment

### Hardware:
- *Customer Devices*: Mobile (Android/iOS), Desktop.
- *Server*: 16-core CPU, 32 GB RAM, SSD storage.

### Software:
- *Frontend*: React/Angular.
- *Backend*: Node.js or Django/Flask.
- *Database*: MongoDB or PostgreSQL.

### Configuration:
- Staging server mirroring production data.
- Mock APIs for early testing.

---

## 7. Test Cases

### Feature: User Registration
*Scenario:* User registers successfully  
*Given:* The user is on the registration page.  
*When:* The user enters valid information (name, email, password).  
*Then:* The user should be successfully registered and redirected to the login page.  

Chai.js Code:
```javascript
const chai = require('chai');
const expect = chai.expect;
const registrationPage = require('../pages/registrationPage');

describe('User Registration', function() {
  it('should register user successfully', function() {
    registrationPage.open();
    registrationPage.fillRegistrationForm('John Doe', 'john@example.com', 'password123');
    registrationPage.submitForm();
    expect(registrationPage.getSuccessMessage()).to.equal('Registration successful');
    expect(browser.getUrl()).to.include('/login');
  });
});
# Blinkit - Test Suite

---

## Feature: User Registration

### Scenario: User registers successfully

#### Description:
Ensure users can register successfully and are redirected to the login page after completion.

### Steps:

1. *Given:*  
   The user is on the registration page.

2. *When:*  
   The user enters valid details such as a valid name, email, and password.

3. *Then:*  
   - The user sees a success message: "Registration successful".  
   - The user is redirected to the login page (/login).

```javascript
const chai = require('chai');
const expect = chai.expect;
const registrationPage = require('../pages/registrationPage');

describe('Blinkit User Registration', function() {
  it('should register the user successfully', function() {
    registrationPage.open();
    registrationPage.fillRegistrationForm('Saloni Sharma', 'saloni@example.com', 'securePassword123');
    registrationPage.submitForm();
    expect(registrationPage.getSuccessMessage()).to.equal('Registration successful');
    expect(browser.getUrl()).to.include('/login');
  });
});
```
# Blinkit - User Login Test

## Feature: User Login

### Scenario: User logs in with valid credentials

*Description:*  
Ensure users can log in successfully and are redirected to the dashboard upon authentication.

### Steps:

*Given:*  
- The user is on the login page.

*When:*  
- The user enters valid credentials (email and password).

*Then:*  
1. The user sees a welcome message: "Welcome, Saloni Sharma".  
2. The user is redirected to the dashboard (/dashboard).

### JavaScript Test Code

```javascript
const chai = require('chai');
const expect = chai.expect;
const loginPage = require('../pages/loginPage');

describe('Blinkit User Login', function() {
  it('should login user successfully', function() {
    loginPage.open();
    loginPage.enterCredentials('saloni@example.com', 'securePassword123');
    loginPage.submitLogin();
    expect(loginPage.getWelcomeMessage()).to.include('Welcome, Saloni Sharma');
    expect(browser.getUrl()).to.include('/dashboard');
  });
});
```
# Blinkit - Product Browsing Test

## Feature: Product Browsing

### Scenario: User browses and searches for products

*Description:*  
Ensure users can browse products, filter by category, and search by product name.

### Steps:

*Given:*  
- The user is on the product catalog page.

*When:*  
1. The user browses the product listings.  
2. The user filters products by category (e.g., "Fruits and Vegetables").  
3. The user searches for a product by name.  

*Then:*  
1. The products are displayed correctly by category.  
2. The search results are accurate based on the product name.

---

### JavaScript Test Code

```javascript
const chai = require('chai');
const expect = chai.expect;
const productPage = require('../pages/productPage');

describe('Blinkit Product Browsing', function() {
  it('should display products filtered by category and search results', function() {
    productPage.open();
    productPage.filterByCategory('Fruits and Vegetables');
    expect(productPage.getFilteredCategory()).to.equal('Fruits and Vegetables');

    productPage.searchProduct('Banana');
    expect(productPage.getSearchResults()).to.include('Banana');
  });
});
```

# Blinkit - Order Placement Test

## Feature: Order Placement

### Scenario: User places an order successfully

*Description:*  
Ensure users can add products to the cart and place an order successfully.

### Steps:

*Given:*  
- The user is logged in and has products in the cart.

*When:*  
1. The user proceeds to checkout.  
2. The user selects a delivery address and payment method.  

*Then:*  
1. The order is successfully placed.  
2. The user sees a confirmation message: "Order placed successfully".  
3. The user is redirected to the order confirmation page (/order-confirmation).

---

### JavaScript Test Code

```javascript
const chai = require('chai');
const expect = chai.expect;
const cartPage = require('../pages/cartPage');

describe('Blinkit Order Placement', function() {
  it('should place an order successfully', function() {
    cartPage.open();
    cartPage.proceedToCheckout('123 Street, Delhi');
    cartPage.selectPaymentMethod('Credit Card');
    cartPage.submitOrder();
    expect(cartPage.getConfirmationMessage()).to.equal('Order placed successfully');
    expect(browser.getUrl()).to.include('/order-confirmation');
  });
});
```

# Blinkit - Profile Management Test

## Feature: Profile Management

### Scenario: User updates profile successfully

*Description:*  
Ensure users can update their profile details successfully.

### Steps:

*Given:*  
- The user is logged in.

*When:*  
- The user updates their profile information (email, name, address).

*Then:*  
1. The profile is updated successfully.  
2. The user sees a confirmation message: "Profile updated successfully".

---

### JavaScript Test Code

```javascript
const chai = require('chai');
const expect = chai.expect;
const profilePage = require('../pages/profilePage');

describe('Blinkit Profile Management', function() {
  it('should update user profile successfully', function() {
    profilePage.open();
    profilePage.updateProfile({
      email: 'saloni@example.com',
      name: 'Saloni Sharma',
      address: '456 New Avenue, Mumbai, India'
    });
    expect(profilePage.getSuccessMessage()).to.equal('Profile updated successfully');
  });
});
```
