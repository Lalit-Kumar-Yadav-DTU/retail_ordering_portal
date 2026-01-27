# retail_ordering_portal
A MERN stack retail ordering app where users browse products, manage carts, and place orders with real-time inventory updates. Uses React, Tailwind CSS, and Redux on the frontend, with Node.js, Express, MongoDB, and JWT (HTTP-only cookies) for secure backend authentication.

#Design Phase - The complete flow 


![complete_flow_chart](https://github.com/user-attachments/assets/a5dbf3e4-cf61-4d0a-859e-9acbc8b24686)

![class_diagram](https://github.com/user-attachments/assets/b610cce9-1789-4d11-a140-c15a6a665198)

Frontend Architecture
Tech Stack

React.js – UI & component-based architecture

Tailwind CSS – responsive styling

Redux – global state management

Axios – API communication

Frontend Responsibilities

Render UI (menu, cart, orders, admin panel)

Manage client-side routing

Store global state (auth, cart, user)

Call backend APIs with credentials

Handle loading & error states

Frontend Structure (Recommended)
src/
 ├── components/
 ├── pages/
 │    ├── Login.jsx
 │    ├── Menu.jsx
 │    ├── Cart.jsx
 │    ├── Orders.jsx
 │    └── AdminDashboard.jsx
 ├── redux/
 │    ├── authSlice.js
 │    ├── cartSlice.js
 │    └── productSlice.js
 ├── services/
 │    └── api.js
 └── App.js

Frontend → Backend Communication

Uses REST APIs

⚙️ Backend Architecture
Tech Stack

Node.js

Express.js

JWT for authentication

bcrypt for password hashing

Mongoose for MongoDB interaction

Backend Responsibilities

Authenticate users (JWT)

Authorize roles (Customer / Admin)

Handle business logic (cart, orders, inventory)

Expose REST APIs

Validate requests & handle errors

Backend Structure (Recommended)
backend/
 ├── controllers/
 ├── routes/
 ├── models/
 ├── middleware/
 │    ├── authMiddleware.js
 │    └── adminMiddleware.js
 ├── config/
 └── server.js

Security Design

JWT stored in HTTP-only cookies

Middleware-based route protection

Role-based authorization

Environment variables for secrets

🗄️ Database Architecture (MongoDB)
Database Type

NoSQL (MongoDB)

Core Collections

users

categories

products

inventory

carts

orders

Relationships (Logical)

User → Cart (1:1)

User → Orders (1:N)

Category → Products (1:N)

Product → Inventory (1:1)

Order → OrderItems (1:N)


🔐 Authentication APIs
POST   /api/auth/register     → Register a new user
POST   /api/auth/login        → Login user and set JWT cookie
POST   /api/auth/logout       → Logout user and clear cookie
GET    /api/auth/me           → Get logged-in user details

📋 Menu & Product APIs (Public)
GET    /api/menu              → Get full menu (categories + products)
GET    /api/categories        → Get all categories
GET    /api/products          → Get products (filter by category)
GET    /api/products/:id      → Get single product details

🛒 Cart APIs (Authenticated User)
GET    /api/cart              → Get user cart
POST   /api/cart/add          → Add item to cart
PUT    /api/cart/update       → Update cart item quantity
DELETE /api/cart/remove/:id   → Remove item from cart
DELETE /api/cart/clear        → Clear cart

📦 Order APIs (Authenticated User)
POST   /api/orders            → Place a new order
GET    /api/orders/my         → Get logged-in user order history
GET    /api/orders/:id        → Get order details

🧑‍💼 Admin APIs (Admin Role Only)
Product Management
POST   /api/admin/products          → Add new product
PUT    /api/admin/products/:id      → Update product
DELETE /api/admin/products/:id      → Disable/Delete product

Category Management
POST   /api/admin/categories        → Add category
PUT    /api/admin/categories/:id    → Update category

Inventory Management
GET    /api/admin/inventory         → View inventory
PUT    /api/admin/inventory/:id     → Update inventory quantity

Order Management
GET    /api/admin/orders            → View all orders
PUT    /api/admin/orders/:id        → Update order status
