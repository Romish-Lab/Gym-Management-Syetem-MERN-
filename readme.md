# Gym Management System (GMS)

A full-stack web application for managing gym operations — built with the MERN stack (MongoDB, Express.js, React.js, Node.js).

## Overview

The Gym Management System is a centralized platform designed to streamline fitness center operations. It provides role-based access for administrators, trainers, and members, enabling efficient management of memberships, class scheduling, payments, and member health data.

## Features

### Member

- Register, login, and manage personal profile
- Browse and enroll in gym classes
- Select membership plans (Basic, Standard, Premium)
- Secure online payments via Stripe
- BMI calculator and health metrics tracking
- Submit reviews and ratings for classes

### Trainer

- Dedicated trainer portal
- View assigned classes and enrolled trainees

### Admin

- Full dashboard with real-time analytics
- Manage members, trainers, and classes (CRUD)
- Process and track memberships
- Moderate class reviews
- Cloud-based image management via Cloudinary

## Tech Stack

| Layer          | Technology                              |
| -------------- | --------------------------------------- |
| Frontend       | React.js, Redux, Material UI, Bootstrap |
| Backend        | Node.js, Express.js                     |
| Database       | MongoDB Atlas (Mongoose ODM)            |
| Authentication | JWT, BcryptJS                           |
| Payments       | Stripe API                              |
| Media Storage  | Cloudinary                              |
| Email          | Nodemailer                              |
| Dev Tools      | Postman, Git, VS Code                   |

## Getting Started

### Prerequisites

- Node.js v18+
- MongoDB Atlas account
- Stripe account
- Cloudinary account

### Installation

```bash
# Clone the repository
git clone https://github.com/ayuushpokharel/gms-GUI.git
cd gms-GUI

# Install backend dependencies
npm install

# Install frontend dependencies
cd frontend && npm install
```

### Environment Variables

Create a `.env` file inside `backend/config/` with the following:

```env
PORT=8000
NODE_ENV=development

MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_jwt_secret
JWT_EXPIRE=7d
COOKIE_EXPIRE=7

STRIPE_API_KEY=your_stripe_api_key
STRIPE_SECRET_KEY=your_stripe_secret_key

CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

SMTP_HOST=smtp.gmail.com
SMTP_PORT=465
SMTP_EMAIL=your_email@gmail.com
SMTP_PASSWORD=your_email_password
```

### Running the App

```bash
# Start backend (from root)
npm run dev

# Start frontend (from /frontend)
npm start
```

The backend runs on `http://localhost:8000` and the frontend on `http://localhost:3000`.
## API Reference
See [API.md](./API.md) for full endpoint documentation.

## Project Structure
