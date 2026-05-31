# Gym Management System (GMS)

A full-stack web application for managing gym operations — built with the MERN stack (MongoDB, Express.js, React.js, Node.js).

## Overview

The Gym Management System is a centralized platform designed to streamline fitness center operations. It provides role-based access for administrators, trainers, and members, enabling efficient management of memberships, class scheduling, payments, and member health data.

## Features

### Member

- Register, login, and manage personal profile
- Browse and filter gym classes by category, price, and rating
- Add classes to cart and enroll via multi-step checkout
- Select membership plans (Basic, Standard, Premium)
- Secure online payments via Stripe
- BMI calculator and health metrics tracking
- Submit and manage class reviews and ratings
- Password reset via email

### Trainer

- Dedicated trainer portal
- View assigned classes and enrolled trainees

### Admin

- Full dashboard with real-time analytics and charts
- Manage members, trainers, and classes (CRUD)
- Process and track memberships (Processing → Active → Expired)
- Moderate and delete class reviews
- Cloud-based image management via Cloudinary

## Tech Stack

| Layer          | Technology                                 |
| -------------- | ------------------------------------------ |
| Frontend       | React.js 18, Redux, Material UI, Bootstrap |
| Backend        | Node.js, Express.js                        |
| Database       | MongoDB Atlas (Mongoose ODM)               |
| Authentication | JWT, BcryptJS                              |
| Payments       | Stripe API                                 |
| Media Storage  | Cloudinary                                 |
| Email          | Nodemailer                                 |
| Dev Tools      | Postman, Git, VS Code                      |

## Getting Started

### Prerequisites

- Node.js v18+
- MongoDB Atlas account
- Stripe account
- Cloudinary account
- Gmail account (for Nodemailer)

### Installation

```bash
# Clone the repository
git clone https://github.com/Romish-Lab/Gym-Management-Syetem-MERN-.git
cd Gym-Management-Syetem-MERN-

# Install backend dependencies
npm install

# Install frontend dependencies
cd frontend && npm install
```

### Environment Variables

Create a `.env` file inside `backend/config/` based on the provided `.env.example`:

```env
PORT=8000
NODE_ENV=development

db=your_mongodb_connection_string

JWT_SECRET=your_jwt_secret
JWT_EXPIRE=7d
COOKIE_EXPIRE=7

SMTP_HOST=smtp.gmail.com
SMPT_SERVICE=gmail
SMPT_MAIL=your_email@gmail.com
SMPT_PASSWORD=your_gmail_app_password

CLOUDINARY_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

STRIPE_API_KEY=your_stripe_publishable_key
STRIPE_SECRET_KEY=your_stripe_secret_key

FRONTEND_URL=http://localhost:3000
```

### Running the App

```bash
# Start backend (from root)
npm run dev

# Start frontend (from /frontend)
npm start
```

The backend runs on `http://localhost:8000` and the frontend on `http://localhost:3000`.

## Project Structure

```
Gym-Management-Syetem-MERN-/
├── backend/
│   ├── config/             # Environment and DB config
│   ├── controllers/        # Route controllers
│   │   ├── classController.js
│   │   ├── membershipController.js
│   │   ├── paymentController.js
│   │   └── userController.js
│   ├── middleware/         # Auth and error handling
│   ├── models/             # Mongoose schemas
│   │   ├── classModel.js
│   │   ├── membershipModel.js
│   │   └── userModel.js
│   ├── routes/             # API routes
│   ├── utils/              # Helper utilities
│   └── server.js
├── frontend/
│   └── src/
│       ├── actions/        # Redux actions
│       ├── components/     # UI components
│       │   ├── Admin/
│       │   ├── Class/
│       │   ├── Membership/
│       │   ├── Trainer/
│       │   ├── User/
│       │   ├── cart/
│       │   └── layout/
│       ├── constants/      # Redux constants
│       ├── reducers/       # Redux reducers
│       ├── utils/          # Helper utilities
│       ├── store.js        # Redux store
│       └── App.js
└── package.json
```

## API Reference

See [API.md](./API.md) for full endpoint documentation.

## User Roles

| Role      | Access                                                   |
| --------- | -------------------------------------------------------- |
| `user`    | Browse classes, purchase memberships, manage own profile |
| `trainer` | Trainer portal, view assigned trainees                   |
| `admin`   | Full access to all resources and dashboard               |

## Membership Plans

| Plan     | Access                     |
| -------- | -------------------------- |
| Basic    | Basic classes only         |
| Standard | Standard and Basic classes |
| Premium  | All classes                |

## Team

| Name            | Roll No. |
| --------------- | -------- |
| Ayush Pokharel  | 800309   |
| Bibek G.C       | 800310   |
| Bikram Kayastha | 800312   |
| Romis Khatiwada | 800333   |

**Khwopa Engineering College, Department of Computer Engineering**
Purbanchal University — Fifth Semester Project
