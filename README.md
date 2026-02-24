# Bookify - Library Management System

Bookify is a modern, full-stack library management system designed to streamline the borrowing process for users and the management process for administrators. Built with React.js and Node.js, it features a responsive UI, real-time notifications, and a robust backend.

## 🚀 Key Features

### User Features (Frontend)
- **Authentication**: Secure Login and Signup with JWT validation.
- **Home Page**:
  - **Featured Books**: Curated list of top books.
  - **Continue Reading**: Quick access to currently borrowed books.
  - **Testimonials**: User reviews and feedback.
- **Catalog & Discovery**:
  - **Full Catalog**: Browse the entire library collection.
  - **Search & Filter**: Find books by title, author, or genre.
  - **Book Details**: View synopsis, author info, and availability status.
- **Library Management**:
  - **Cart System**: Add books to cart and checkout (issue) them in bulk.
  - **Borrowing**: Issue books for a fixed 14-day period.
  - **Return System**: Easy return process via a dedicated modal with instant library updates.
- **Profile Dashboard**:
  - **Reading Stats**: Track "Total Reads" and "Books Returned".
  - **History**: View a complete log of all past borrowed books.
  - **Notifications**: Real-time alerts for due dates, payments, and stock availability.
  - **Membership**: View current plan details (Student/Gold/Diamond).
- **Notifications**:
  - Real-time alerts for Book Issued, Returned, Payment Received, and Out of Stock.
  - Email notifications for stock availability (Waitlist).

### Admin Features (Back Office)
- **Dashboard**:
  - **Overview**: At-a-glance stats for Total Users, Books, Issued Books, and Revenue.
  - **Trends**: Visual graphs for monthly borrowing trends.
- **Book Management**:
  - **CRUD Operations**: Add, Edit, and Delete books.
  - **Stock Control**: Manage inventory levels.
- **User Management**:
  - **User List**: View and manage registered users.
  - **Membership Control**: Update user plans and roles.
- **Transaction Management**:
  - **Issues**: Track all active and past book issues.
  - **Returns**: Process manual returns if needed.
- **Reviews**: Monitor and moderate user-submitted reviews.
- **Settings**: Configure system preferences and admin profile.

---

## 🛠 Tech Stack

### Frontend
- **Framework**: React 18 (Vite)
- **Styling**: Tailwind CSS, Lucide React (Icons)
- **State Management**: React Hooks (useState, useEffect, Context API)
- **HTTP Client**: Axios
- **Routing**: React Router DOM v6
- **Animations**: CSS Transitions, Canvas Confetti

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB (Mongoose ODM)
- **Authentication**: JWT (JSON Web Tokens), Bcrypt (Password Hashing)
- **Validation**: Joi / Validator models

---

## 📂 Project Structure

```
Bookify/
├── backend/                # Node.js API Server
│   ├── config/             # DB Connection
│   ├── controllers/        # Logic (Auth, Books, Users, Notifications)
│   ├── middleware/         # Auth & Error Handling
│   ├── models/             # Mongoose Schemas (User, Book, Order, Notification)
│   ├── routes/             # API Endpoints
│   └── server.js           # App Entry Point
│
├── frontend/               # User-Facing React App
│   ├── src/
│   │   ├── components/     # Reusable UI (Navbar, Cards, Modals)
│   │   ├── pages/          # Main Views (Home, Catalog, Profile, Cart)
│   │   ├── utils/          # Helpers (Date formatting, API config)
│   │   └── App.jsx         # Router Config
│
├── admin/                  # Admin Dashboard React App
│   ├── src/
│   │   ├── pages/          # Admin Views (Books, Users, Stats)
│   │   └── components/     # Admin Layout & Widgets
│   └── index.html
```

---

## 🔧 Installation & Setup

### Prerequisites
- Node.js (v16+)
- MongoDB (Local or Atlas)
- NPM

### 1. Clone the Repository
```bash
git clone <repository-url>
cd Bookifyyy
```

### 2. Backend Setup
```bash
cd backend
npm install
```
Create a `.env` file in `/backend`:
```env
PORT=5001
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
```
Start the server:
```bash
npm run dev
```

### 3. Frontend Setup
```bash
cd ../frontend
npm install
```
Create a `.env` file in `/frontend`:
```env
VITE_API_URL=http://localhost:5001/api
```
Start the user app:
```bash
npm run dev
```

### 4. Admin Setup
```bash
cd ../admin
npm install
```
Create a `.env` file in `/admin`:
```env
VITE_API_URL=http://localhost:5001/api
```
Start the admin dashboard:
```bash
npm run dev
```

---

## 📜 Development History & Changelog

### 🚀 New Features

#### 🔔 Notification System
- **Backend**:
    - Implemented `Notification` model with `userId` support for targeted alerts.
    - Created API endpoints for fetching, creating, and marking notifications as read.
    - Integrated triggers for: Registration, Book Issued/Returned, Payments, Membership Upgrades, Stock Alerts.
- **Frontend**:
    - **Notification Dropdown**: Added to Navbar for quick access.
    - **Notifications Page**: Dedicated page (`/notifications`) with filters.
    - **Real-time Polling**: Auto-refresh every 3s.

#### 📚 Reading & Library Management
- **Reading Section**: "Continue Reading" on Home Page, "Read Again" functionality.
- **Return Book Modal**: Instant return processing with optimistic UI updates.
- **Stock Restoration**: Returning a book automatically replenishes stock.
- **Duplicate Prevention**: Logic to prevent double-issuing the same book.

#### 👤 Profile Enhancements
- **Stats**: "Total Reads" and "Returned Books" connected to backend.
- **Role Badge**: Dynamic user role display (Student/Admin).
- **History Tab**: Complete borrowing log.

#### 📦 Stock Management
- **Notify Me**: Waitlist system for out-of-stock books.
- **Email Alerts**: Automated emails when stock is replenished.

### 🐛 Bug Fixes
- **Profile Visibility**: Fixed `useState` hook crash in `ProfilePage.jsx`.
- **Image Handling**: Added fallbacks for broken book covers across all pages.
- **Return Modal**: Fixed crash due to undefined error state.
- **Data Logic**: Corrected overdue calculations and return counters.

---

### 🌟 Features (Part 2) - Recent Updates

#### 💬 Community Reviews System
- **Frontend**:
    - **Interactive Marquee**: Infinite scrolling display of user reviews.
    - **Review Cards**: Glassmorphism design with 5-star ratings and user details.
    - **Write Review Modal**: User-friendly form to submit feedback.
    - **Review Details**: Pop-up modal to view full review content and rate helpfulness.
- **Backend**:
    - **WebsiteReview Model**: Schema for storing user feedback and ratings.
    - **API Endpoints**: CRUD operations for fetching, creating, and rating reviews.
    - **Dynamic Data**: Mix of real user reviews and demo data for initial population.

#### 💼 Business & Career Applications
- **Application Forms**: Dedicated modals for:
    - **Partner**: For libraries and institutions.
    - **Publisher**: For authors and publishing houses.
    - **Developer**: For tech talent (includes CV upload).
    - **Moderator**: For community management.
- **File Uploads**: Secure PDF CV upload via `multer`.
- **Admin Panel**: View and download applicant details and CVs.
- **Email Notifications**: Automated confirmation emails to applicants.

#### 🎨 UI/UX Overhauls
- **Auth Page**:
    - 50/50 Split layout with dynamic background.
    - Glassmorphism form card with premium inputs.
    - Password visibility toggle & "Forgot Password" OTP flow.
- **Reading Page**:
    - "My Reading List" header with gradient typography.
    - Scroll-to-top behavior on navigation.
- **Responsive Design**:
    - Optimized layouts for Mobile, Tablet, and Desktop across all pages.
    - Adaptive Navbar with hamburger menu.

#### 🛠 Technical Improvements
- **Build Optimization**: Configured `manualChunks` in Vite to reduce bundle size by 50%.
- **Cross-Device Access**: configured API URLs for LAN access during testing.
- **Footer Enhancements**: Added Policy Modals (Terms, Privacy, Cookies) and improved layout.

---

## 📄 License
MIT License