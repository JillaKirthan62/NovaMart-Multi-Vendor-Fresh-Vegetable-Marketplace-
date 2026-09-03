Link [ https://nova-mart-multi-vendor-fresh-vegeta.vercel.app/]
# 🥬 NovaMart — Multi-Vendor Fresh Vegetable Marketplace

<p align="center">
  <strong>A modern multi-vendor marketplace for buying fresh vegetables from local farmers and vendors.</strong>
</p>

<p align="center">
  <a href="https://nova-mart-multi-vendor-fresh-vegeta.vercel.app/">🌐 Live Demo</a>
</p>

📌 Overview

NovaMart is a browser-based multi-vendor e-commerce platform designed specifically for fresh vegetable retail.

The platform brings customers, independent sellers/farmers, and administrators together through a single digital marketplace. Customers can browse and search vegetables, filter products by category, manage a shopping cart, edit delivery details, choose a payment method, place orders, and track delivery status.

The project was developed as part of the Zidio Development — UI/UX & Full-Stack Design Domain program.

Project Codename: NovaMart
Version: 1.0
Documentation Date: 25 June 2026

🌐 Live Website

Try NovaMart:
https://nova-mart-multi-vendor-fresh-vegeta.vercel.app/

✨ Key Features

🛒 Customer Features

Browse a catalog of 38 vegetables

Search vegetables by name

Filter products by category

View product details, seller information, price, unit, and rating

Add products to cart

Remove products from cart

Increase/decrease product quantities

Live subtotal, tax, and total calculation

Edit delivery address during checkout

Cash on Delivery (COD)

Online payment options:

UPI

Card

Net Banking

Sign up and sign in

Email verification using OTP flow

Password reset flow

Order confirmation

Order tracking

Responsive, mobile-friendly interface

🏪 Seller Features

Seller dashboard

Product listing

Stock management

Incoming order management

Order status updates

Order fulfilment workflow

👨‍💼 Admin Features

User management

Product/catalog moderation

Platform oversight

Reports and analytics

The documented architecture supports three main roles: Customer, Seller, and Admin.

🥕 Product Categories

NovaMart organizes its catalog into five categories:

Category

Description

🥬 Leafy Greens

Fresh leafy vegetables

🥕 Root Vegetables

Root and underground vegetables

🎃 Gourds & Squashes

Gourds and squash varieties

🥑 Exotic & Others

Exotic and other vegetables

🌿 Herbs & Aromatics

Herbs and aromatic produce

🔄 Customer Journey

Home
  ↓
Browse / Search
  ↓
Category Filter
  ↓
Product Details
  ↓
Add to Cart
  ↓
Cart
  ↓
Checkout
  ↓
Edit Delivery Address
  ↓
Choose Payment Method
  ↓
Place Order
  ↓
Order Tracking
  ↓
Delivery

The core customer journey is:

Browse → Cart → Checkout → Track

📦 Order Lifecycle

Orders follow a defined lifecycle:

Placed
  ↓
Confirmed
  ↓
Packed
  ↓
Out for Delivery
  ↓
Delivered

A cancellation path is also supported.

The seller-facing workflow handles confirmation, packing, and handover to delivery.

💳 Payment Flow

NovaMart supports two payment paths:

Cash on Delivery

Checkout
   ↓
Select COD
   ↓
Create Order
   ↓
Payment Recorded
   ↓
Order Processing

Online Payment

Checkout
   ↓
Select Online Payment
   ↓
UPI / Card / Net Banking
   ↓
Payment Gateway
   ↓
Payment Confirmation
   ↓
Order Confirmation

The documented backend design includes payment initiation and a payment-gateway webhook for updating payment status.

🏗️ System Architecture

NovaMart is designed around a layered client-server architecture.

┌──────────────────────────────────────────────┐
│                 CLIENT LAYER                 │
│                                              │
│ Customer Web App │ Mobile PWA │ Seller Portal│
└──────────────────────┬───────────────────────┘
                       │
                       ▼
                ┌─────────────┐
                │ API Gateway │
                └──────┬──────┘
                       │
        ┌──────────────┼──────────────┐
        ▼              ▼              ▼
   Auth Service   Catalog Service  Order Service
        │              │              │
        └──────────────┼──────────────┘
                       │
                Payment Service
                       │
                Notification Service
                       │
                       ▼
        ┌─────────────────────────────┐
        │          DATA LAYER         │
        │                             │
        │ PostgreSQL │ Redis │ Storage│
        └─────────────────────────────┘

The documented architecture separates the client, application services, and data layer, with API-based communication between the frontend and backend.

🧰 Technology Stack

Frontend

HTML5

CSS3

JavaScript (ES6+)

Responsive web design

Client-side state management

Fetch / REST API communication

Backend — Target / Documented Architecture

Node.js

Express.js

REST API

Sequelize ORM

JWT authentication

bcrypt password hashing

Helmet

CORS

Express Rate Limit

Database & Infrastructure

PostgreSQL

Redis

Cloud-hosted application servers

CDN / DNS

Load balancer

Media storage

Development & Documentation

Git

GitHub

Mermaid.js

Matplotlib

Word/DOCX documentation

Note: The deployed prototype demonstrates the browser-based frontend. The project documentation also describes the intended REST backend, database, payment, notification, and deployment architecture.

🧩 Frontend Modules

The frontend is organized around independent modules:

Frontend
├── Navigation
├── Catalog
│   ├── Product Listing
│   ├── Search
│   └── Category Filtering
├── Product Details
├── Cart
│   ├── Add Item
│   ├── Remove Item
│   └── Quantity Management
├── Checkout
│   ├── Delivery Address
│   └── Payment Selection
├── Authentication
│   ├── Sign In
│   ├── Sign Up
│   ├── Email Verification
│   └── Password Reset
└── Order Tracking

🔐 Security Design

The documented backend architecture includes several security measures:

HTTPS for payment and sensitive data transmission

Passwords stored using salted hashes

JWT-based authentication

Role-based authorization

Expiring authentication tokens

Protected API routes

Payment webhook signature verification

Rate limiting

Secure HTTP headers using Helmet

Server-side validation of product price and stock

Database transactions for order creation

The backend is designed so that authoritative values such as product price, stock, order status, and payment status are controlled by the server rather than trusted from the client.

🗄️ Database Design

The documented relational data model contains the following core entities:

Users
 ├── Sellers
 ├── Orders
 │    ├── Order Items
 │    └── Payment
 └── Addresses

Sellers
 └── Products

Products
 └── Order Items

Core Tables

Table

Purpose

users

Customer, seller, and admin accounts

sellers

Seller/farm profiles

products

Vegetable catalog and stock

orders

Customer orders

order_items

Items belonging to orders

payments

COD and online payment records

addresses

Customer delivery addresses

🔌 Documented API Structure

The project documentation defines REST endpoints organized by service.

Authentication

POST /api/auth/register
POST /api/auth/login
POST /api/auth/verify-email

Products / Catalog

GET /api/products
GET /api/products/:id

Supports category filtering and keyword search.

Example:

GET /api/products?category=Leafy+Greens&q=spinach

Orders

POST /api/orders
PATCH /api/orders/:id/status

Payments

POST /api/payments/initiate
POST /api/payments/webhook

🧪 Testing

The project documentation records both unit and functionality testing.

Unit Testing

Tested areas include:

Adding an item to an empty cart

Quantity minimum validation

Cart total calculation

Insufficient stock handling

Invalid order-status rejection

JWT tampering rejection

Functionality Testing

Tested flows include:

Catalog search

Category filtering

Cart item removal

Checkout address editing

Online payment selection

Order placement and tracking

Global navigation/back button

Sign-up and email verification

The documented test cases are marked as Pass.

🚀 Getting Started

Prerequisites

For the documented full-stack architecture:

Node.js

npm

PostgreSQL

Redis

Git

Clone the Repository

git clone https://github.com/<your-username>/novamart.git
cd novamart

Install Dependencies

npm install

Environment Variables

Create a .env file for backend configuration.

Example:

PORT=4000
DATABASE_URL=your_database_url
REDIS_URL=your_redis_url
JWT_SECRET=your_jwt_secret
PAYMENT_GATEWAY_KEY=your_payment_gateway_key

Do not commit real credentials or secrets to GitHub.

Run the Application

If the repository contains the documented Node.js/Express backend:

npm start

For frontend-only development, open the project's main HTML entry point using a local development server.

🌍 Deployment

The live frontend prototype is deployed on Vercel.

The documented production architecture supports:

User
  ↓
DNS / CDN
  ↓
Load Balancer
  ↓
Application Servers
  ↓
API Services
  ↓
PostgreSQL + Redis + Media Storage

The architecture is designed to support horizontal scaling by running multiple application server instances behind a load balancer.

🌱 Project Objectives

NovaMart was created to address three major problems in local vegetable retail:

Fragmented supply — bring multiple local sellers into one marketplace.

Opaque logistics — provide visible order status from placement to delivery.

Limited payment options — support both COD and online payment methods.

The solution focuses specifically on produce-related requirements such as category browsing, unit-based pricing, freshness, local sellers, cart management, and fast delivery workflows.

📈 Future Enhancements

The documented product roadmap identifies potential future improvements including:

Seller analytics dashboard

Wishlist

Subscription vegetable baskets

Regional expansion

Enhanced order tracking

Vendor payout module

Additional marketplace capabilities

🗂️ Suggested Repository Structure

A clean repository can follow this structure:

NovaMart/
│
├── frontend/
│   ├── index.html
│   ├── css/
│   ├── js/
│   └── assets/
│
├── backend/
│   ├── server.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── catalog.js
│   │   ├── orders.js
│   │   └── payments.js
│   ├── models/
│   ├── middleware/
│   ├── services/
│   └── db/
│
├── diagrams/
├── docs/
├── tests/
├── .env.example
├── .gitignore
└── README.md

Adjust this structure to match the actual files in your GitHub repository.

🌿 Design Approach

NovaMart followed an iterative, prototype-first methodology:

Research & Discovery

UI Design & Visual System

Prototyping & Interaction

Testing, Handoff & Documentation

The project documentation describes an Agile-style approach based on short iterations, continuous feedback, and incremental delivery.

📚 Documentation

The complete project report contains:

Requirements analysis

Functional and non-functional requirements

System architecture

Client-server architecture

Database and ER diagrams

Sequence diagrams

State diagrams

Business process flows

Customer journey

Git workflow

Project planning

Analytics and business diagrams

Implementation details

API design

Testing results

Technical manual

User guide

The report contains 49 supporting diagrams covering architecture, data modelling, process flows, state management, planning, analytics, and strategic views.

👨‍💻 Author

Jilla Kirthan

B.Tech — Computer Science & Engineering
Specialization: Artificial Intelligence & Machine Learning
SR University, Warangal, Telangana

🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test your changes
5. Commit your changes
6. Push the branch
7. Open a Pull Request

Example:

git checkout -b feature/new-feature
git add .
git commit -m "Add new feature"
git push origin feature/new-feature

📄 License

Add the license that applies to your repository before publishing this project publicly.

⭐ Support

If you find NovaMart useful or interesting, consider giving the repository a ⭐ on GitHub.

<p align="center">
  <strong>NovaMart — Fresh vegetables. Multiple sellers. One marketplace. 🥬</strong>
</p>
