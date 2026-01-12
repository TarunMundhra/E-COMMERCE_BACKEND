# 🛒 E-Commerce Backend  
### ASSIGNMENT_BACKEND

This repository contains the backend of an e-commerce application built using **Node.js, Express.js, MongoDB (Mongoose)** with **JWT authentication** and **Cloudinary** for media storage.

The project implements role-based access control, cart-based ordering, and admin-specific operations as required by the assignment.

---

## 🚀 Features Implemented

### 🔐 Authentication & Authorization
- User registration with two roles: `USER` and `ADMIN`
- JWT-based access token authentication
- Refresh token mechanism implemented
- Admin-only routes protected via middleware

### 🧑‍💼 Admin Functionality
- Admin middleware implemented
- Admin-specific operations across controllers
- Any admin can delete products (ownership validation not enforced yet)

### 📦 Product Management
- Product creation and deletion
- Product image upload using **Cloudinary**
- Old product images are deleted from Cloudinary when updated
- `findOneAndDelete()` returns deleted document (expected behavior)

### 🛒 Cart & Orders
- No separate Cart model
- Cart is embedded inside `User` schema as an array
- Orders can be placed **only via cart**
- On order placement:
  - Cart is cleared
  - Product stock is reduced
  - Order status is stored
  - Address is mandatory for each order
- Order status maintained

---

## ⚙️ Technical Design Notes

- Cart logic handled inside User Controller
- Admin logic spread across controllers (needs refactor)
- `dotenv` initially loaded after Cloudinary config (fixed)
- Refresh token field added later to User schema
- Cloudinary folder path intentionally not used
- GET ALL PRODUCTS route is public
- Admin access token requires fresh admin login
- CORS origin currently set to localhost
- `isUserLoggedIn` helper not implemented yet

---

## 🧩 Tech Stack

- Node.js
- Express.js
- MongoDB + Mongoose
- JWT Authentication
- Cloudinary
- dotenv

---

## 🛠️ Environment Setup

Create a `.env` file in the root directory:

```env
PORT=8000

MONGODB_URI=your_mongodb_connection_string

ACCESS_TOKEN_SECRET=your_access_token_secret
REFRESH_TOKEN_SECRET=your_refresh_token_secret
ACCESS_TOKEN_EXPIRY=15m
REFRESH_TOKEN_EXPIRY=7d

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

CORS_ORIGIN=http://localhost:5174
```

---

## Frontend

- React 19
- Vite
- TypeScript
- React Router DOM
- Axios

---

## Backend Setup
```
cd Backend
npm i
npm run seed
npm run dev
```

## Frontend Setup
```
cd Frontend
npm i
npm run dev
```
---
