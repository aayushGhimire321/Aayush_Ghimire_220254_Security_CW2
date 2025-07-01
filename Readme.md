**🎟️ Movie Ticketing System**

This project is a Movie Ticketing System built with the MERN Stack — MongoDB, Express.js, React, and Node.js. It delivers a secure, scalable, and responsive platform for cinema‑goers to book seats while giving admins full control over shows, analytics, and payments.

**📑 Table of Contents**

**Features

Installation

Backend Setup

Frontend Setup

Frontend Overview

Backend Overview

Security Design Principles

Usage

Notes

**Feedback**




**🚀 Features**

🔐 Authentication & Authorisation (JWT + Session)

🧑‍💼 Role‑Based Access Control (Admin / User)

🎬 Movie & Show Management (CRUD)

🎟️ Interactive Seat Selection & Ticket Booking

💳 Payment Gateway Integration (e.g. Khalti)

📊 Admin Dashboard with Real‑Time Analytics

📱 Responsive UI (mobile‑friendly)

🔔 Toast Notifications for instant feedback

🛡️ Brute‑Force Protection & Audit Logging

**⚙️ Installation**

**🔧 Prerequisites**

Node.js & npm

MongoDB (local instance or MongoDB Atlas)

**🔙 Backend Setup**

cd backend        # 1. navigate to backend folder
npm install       # 2. install dependencies

**Create a .env file in backend/:**

REACT_APP_API_URL=http://localhost:5000
PORT=5000
MONGODB_CLOUD=your_cloud_mongodb_connection_string
MONGODB_LOCAL=your_local_mongodb_connection_string
JWT_SECRET=your_jwt_secret
JWT_EXPIRY=7d
KHALTI_SECRET_KEY=your_khalti_secret_key
KHALTI_GATEWAY_URL=https://khalti.com/api/v2/payment/verify/
ALLOWED_ORIGINS=https://localhost:3000,https://localhost:5000
EMAIL_USER=your_email
EMAIL_PASS=your_email_password

Then run:

npm start         # 3. start backend (http://localhost:5000)

**🖥️ Frontend Setup**

cd frontend       # 1. navigate to frontend folder
npm install       # 2. install dependencies
npm start         # 3. start React dev server (http://localhost:3000)

**🖼️ Frontend Overview**

Built with React and powered by:

Library

Purpose

Material UI (MUI)

Theme & responsive components

React Router

Single‑page navigation

Axios

API communication

React Toastify

Notifications

ProtectedRoute component

Role‑based route guarding

File highlights

App.js: Declares public + protected routes, MUI theme provider, ToastContainer.

components/: Shared UI (Navbar, Footer, Charts …).

pages/: Split into Public, User, Admin sections.

ProtectedRoute.js: Wrapper enforcing JWT + role checks.




**🔧 Backend Overview**

Powered by Node.js + Express with:

Mongoose ODM (Users, Movies, Bookings …)

JWT for stateless sessions & express‑session for optional server sessions

bcrypt for password hashing

express‑rate‑limit for IP‑based brute‑force blocking

Custom per‑user lockout after repeated failures

Winston / Morgan‑style logging middleware

mongo‑sanitize & JOI for validation / sanitisation




**📡 Key API Endpoints**

Area

Routes

Auth

POST /api/auth/register, POST /login, POST /otp/verify, POST /forgot-password

Movies & Shows

CRUD: GET /api/movies, POST /api/movies …

Bookings

POST /api/book, GET /api/bookings/:id

Admin Analytics

GET /api/admin/stats

Refer to backend/routes/ for full route definitions.




Here’s your updated **🔐 Security Design Principles** section with a bit more clarity and detail, incorporating the existing concepts clearly:

---

### 🔐 Security Design Principles

1. **Authentication & Authorization**

   * JWT-based authentication with secure HTTP-only cookies
   * Optional server-side session management
   * Role-based access control enforced via middleware guards

2. **Input Sanitization & Validation**

   * Use of `mongo-sanitize` to prevent NoSQL injection
   * Schema validation with JOI to ensure data integrity and block XSS attacks

3. **Brute-Force Protection**

   * IP-based throttling with `express-rate-limit` to limit repeated login attempts
   * (Optional) per-account lockout can be added to enhance security further

4. **Password Security**

   * Password hashing using bcrypt with salts
   * Support for password history and expiry policies to enforce password rotation

5. **Audit Logging**

   * Middleware logs all user and admin actions, including access attempts and errors
   * Logs provide traceability for security reviews and forensic analysis

6. **Secure Communication**

   * Enforce HTTPS in production environments to protect data in transit
   * Configure CORS policies with `withCredentials` enabled for secure cross-origin requests

7. **Centralized Error Handling**

   * Uniform JSON response format for errors
   * Sensitive information is never exposed in error messages to clients

---





**💻 Usage**

# 1️⃣  Start MongoDB & backend
cd backend && npm start

# 2️⃣  In a new terminal, start frontend
cd frontend && npm start

Open http://localhost:3000 and:

Register as a user or login as an admin

Browse movies, pick seats, pay via Khalti sandbox

Visit /admin to manage shows & view analytics

**📝 Notes**


Ensure MongoDB is accessible (local URI or Atlas).

For production:

Store secrets securely (env vars / secrets manager).

Enable HTTPS (SSL/TLS).

Configure email (SMTP) & payment gateway credentials.

Max file size for avatar uploads is configurable via MAX_FILE_SIZE env var.

**📬 Feedback**

Questions, bugs, or feature requests? Open an issue or send a pull request — contributions are welcome!

