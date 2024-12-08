# Blinkit 

## Overview

### Project Name
**Blinkit**

### Objective
A grocery delivery web and mobile app, similar to Blinkit.

### Users
- General users (customers)
- Store owners
- Admin

## Features

### User Features
- User Authentication
- Store Search
- Product Browsing
- Cart Management
- Order Placement
- Order Tracking
- Review & Rating

### Store Features
- Store Registration
- Product Management
- Order Management
- Analytics Dashboard

### Admin Features
- User Management
- Store Management
- Order Monitoring
- Reports & Analytics

## Tech Stack

| Layer       | Technologies                                |
|-------------|---------------------------------------------|
| **Frontend**| React.js, Recoil, Tailwind CSS              |
| **Backend** | Node.js, Express.js, MongoDB                |
| **Tools**   | Stripe, Google Maps API, AWS S3, Socket.IO  |

## Setup Instructions


### Step 1; Fork the Repo
### Step 2: Clone the forked Repo
```bash
git clone https://github.com/username/blinkit-clone.git
 ```
### Step 3: Install all dependencies on the backend
```bash
cd server && npm install
```
### Step 4: Install all dependencies on the frontend
```bash
cd ../client && npm install
```
### Step 5: Run the backend 
```bash
cd ../server && npm run start
```
### Step 6: Run the frontend
```bash
cd ../client && npm run dev
```
## Usage Guide

| Task                 | URL/Action                                         |
|----------------------|----------------------------------------------------|
| **User Registration**| `/signup`                                          |
| **Explore Stores**   | Use search bar on the homepage                     |
| **Place an Order**   | Browse products, add to cart, and checkout         |
| **Track Order**      | Real-time updates from confirmation to delivery    |
| **Store Dashboard**  | Manage products, view orders, update order status  |

## API Documentation

| Endpoint                | Description                                |
|-------------------------|--------------------------------------------|
| `POST /auth/register`   | Register a new user.                       |
| `POST /auth/login`      | Authenticate a user.                       |
| `GET /items`            | Get a list of all items available.         |
| `GET /items/:id`        | Get detailed info of a specific item.     |
| `POST /orders`          | Place a new order.                         |
| `GET /orders/:id`       | Get order details.                         |
