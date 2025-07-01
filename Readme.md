

# 🎟️ Movie Ticketing System

A secure, scalable, and responsive **Movie Ticketing System** built with the **MERN Stack** (MongoDB, Express.js, React, Node.js). This platform enables cinema-goers to book seats effortlessly, while providing admins full control over shows, analytics, and payments.

---

## 📑 Table of Contents

* [Features](#-features)
* [Installation](#-installation)

  * [Prerequisites](#-prerequisites)
  * [Backend Setup](#-backend-setup)
  * [Frontend Setup](#-frontend-setup)
* [Frontend Overview](#-frontend-overview)
* [Backend Overview](#-backend-overview)
* [API Endpoints](#-key-api-endpoints)
* [Security Design Principles](#-security-design-principles)
* [Usage](#-usage)
* [Notes](#-notes)
* [Feedback](#-feedback)

---

## 🚀 Features

* 🔐 **Authentication & Authorization** (JWT + Sessions)
* 🧑‍💼 **Role-Based Access Control** (Admin / User)
* 🎬 **Movie & Show Management** (CRUD operations)
* 🎟️ **Interactive Seat Selection & Ticket Booking**
* 💳 **Payment Gateway Integration** (e.g., Khalti)
* 📊 **Admin Dashboard** with real-time analytics
* 📱 **Responsive UI** — mobile-friendly
* 🔔 **Toast Notifications** for instant feedback
* 🛡️ **Brute-Force Protection** & audit logging

---

## ⚙️ Installation

### 🔧 Prerequisites

* Node.js & npm
* MongoDB (local instance or MongoDB Atlas)

---

### 🔙 Backend Setup

```bash
cd backend
npm install
```

Create a `.env` file in the `backend/` directory with the following variables:

```env
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
```

Start the backend server:

```bash
npm start
```

Runs on: [http://localhost:5000](http://localhost:5000)

---

### 🖥️ Frontend Setup

```bash
cd frontend
npm install
npm start
```

Runs on: [http://localhost:3000](http://localhost:3000)

---

## 🖼️ Frontend Overview

Built with **React** using these core libraries:

| Library           | Purpose                            |
| ----------------- | ---------------------------------- |
| Material UI (MUI) | Theming & responsive UI components |
| React Router      | Client-side routing                |
| Axios             | API communication                  |
| React Toastify    | Notifications                      |
| ProtectedRoute    | Role-based route guarding          |

**Key files & folders:**

* `App.js` — Defines public & protected routes, MUI theme provider, ToastContainer
* `components/` — Shared UI components (Navbar, Footer, Charts, etc.)
* `pages/` — Separated by Public, User, Admin sections
* `ProtectedRoute.js` — Wraps routes enforcing JWT + role checks

---

## 🔧 Backend Overview

Built with **Node.js** and **Express** featuring:

* **Mongoose ODM** for database modeling (Users, Movies, Bookings, etc.)
* JWT for stateless authentication + optional `express-session` support
* bcrypt for password hashing
* `express-rate-limit` for IP-based brute-force protection
* Custom user lockout after repeated failed login attempts
* Logging middleware (Winston/Morgan-style)
* Input validation & sanitization using `mongo-sanitize` & JOI

---

## 📡 Key API Endpoints

| Area            |Routes                                                                                |
| -------------- | ----------------------------------------------------------------------------------- |
| Auth           | `POST /api/auth/register`, `POST /login`, `POST /otp/verify`, `POST /forgotpassword`|
| Movies & Shows | CRUD endpoints: `GET /api/movies`, `POST /api/movies`, etc.                         |
| Bookings        | `POST /api/book`, `GET/api/bookings/:id`                                           |
| Admin Analytics | `GET/api/admin/stats`                                                              |

For full route definitions, see `backend/routes/`.

---

## 🔐 Security Design Principles

1. **Authentication & Authorization**

   * JWT-based auth with secure HTTP-only cookies
   * Optional server-side sessions
   * Role-based access control via middleware

2. **Input Sanitization & Validation**

   * `mongo-sanitize` to prevent NoSQL injection
   * JOI schema validation to ensure data integrity and block XSS

3. **Brute-Force Protection**

   * IP throttling with `express-rate-limit`
   * Optional per-account lockouts after repeated failures

4. **Password Security**

   * bcrypt password hashing with salts
   * Support for password history and expiry policies

5. **Audit Logging**

   * Middleware logs all user/admin actions, access attempts, and errors
   * Logs enable traceability and forensic analysis

6. **Secure Communication**

   * HTTPS enforced in production
   * CORS configured with credentials for secure cross-origin requests

7. **Centralized Error Handling**

   * Uniform JSON error responses
   * No sensitive data exposed in error messages

---

## 💻 Usage

1. **Start MongoDB and Backend:**

```bash
cd backend
npm start
```

2. **In a new terminal, start Frontend:**

```bash
cd frontend
npm start
```

3. Open [http://localhost:3000](http://localhost:3000) in your browser.

* Register as a user or log in as an admin
* Browse movies, select seats, and pay via Khalti sandbox
* Visit `/admin` for show management and analytics dashboard

---

## 📝 Notes

* Ensure MongoDB is running and accessible (local or Atlas)
* For production deployment:

  * Store secrets securely (environment variables or secret managers)
  * Enable HTTPS with SSL/TLS certificates
  * Configure SMTP for email and payment gateway credentials properly
* Max avatar upload file size is configurable via `MAX_FILE_SIZE` environment variable

---

## 📬 Feedback

Questions, bugs, or feature requests? Please open an issue or submit a pull request. Contributions are warmly welcome!

