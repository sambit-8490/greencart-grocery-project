# 🌿 Naturify – Full Stack Grocery Project

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Folder Structure](#folder-structure)  
3. [Environment Variables](#environment-variables)  
4. [Setup & Run (Docker)](#setup--run-docker)  
5. [Frontend Development](#frontend-development)  
6. [Backend Development](#backend-development)  
7. [Admin / Seller Access](#admin--seller-access)  
8. [Automatic Admin Creation](#automatic-admin-creation)  
9. [Security Notes](#security-notes)  
10. [Production Deployment](#production-deployment)  

---

## Project Overview

Naturify is a full-stack grocery application with:

- **Frontend**: React + Vite  
- **Backend**: Node.js + Express + MongoDB  
- **Features**: Products, Cart, Orders, Seller/Admin management  
- **Third-party services**: Cloudinary for image storage, Stripe for payments  

---

## Folder Structure

greencart/
├── client/
│ ├── Dockerfile
│ ├── src/
│ ├── public/
│ └── .env
├── server/
│ ├── Dockerfile
│ ├── configs/
│ │ ├── db.js
│ │ └── cloudinary.js
│ ├── controllers/
│ ├── models/
│ ├── routes/
│ ├── .env
│ └── server.js
├── docker-compose.yml
└── README.md

makefile
Copy code

---

## Environment Variables

### **Backend (`server/.env`)**

```env
JWT_SECRET=your_jwt_secret
NODE_ENV=development
PORT=4000

# Admin Credentials
SELLER_EMAIL=admin@example.com
SELLER_PASSWORD=your_admin_password

# MongoDB Setup (docker-compose local)
MONGODB_URI=mongodb://root:rootpassword@mongodb:27017/greencart?authSource=admin

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_cloud_api_key
CLOUDINARY_API_SECRET=your_cloud_api_secret

# Stripe
STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret
Frontend (client/.env)
env
Copy code
VITE_CURRENCY='$'
VITE_BACKEND_URL="http://localhost:4000"
Setup & Run (Docker)
Build and start containers:

bash
Copy code
docker compose up --build
Backend → http://localhost:4000

Frontend → http://localhost:5173

MongoDB → localhost:27017

Stop containers:

bash
Copy code
docker compose down -v
-v removes old volumes to reset MongoDB.

Frontend Development
bash
Copy code
cd client
npm install
npm run dev
Runs on http://localhost:5173

Backend Development
bash
Copy code
cd server
npm install
npm run dev
Runs on http://localhost:4000

Make sure .env exists and is correct

Admin / Seller Access
Open in browser:

bash
Copy code
http://localhost:5173/seller
Email: admin@example.com

Password: (from .env or auto-created in MongoDB)

You can access:

Add Product → /seller/add-product

View Orders → /seller/orders

Product List → /seller/product-list

