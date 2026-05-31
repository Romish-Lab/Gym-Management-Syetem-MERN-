# API Documentation — Gym Management System

Base URL: `http://localhost:8000/api/v1`

All protected routes require a valid JWT token stored in an `access_token` cookie, set automatically on login or registration.

---

## Auth & User Routes

### Public Routes

| Method | Endpoint | Description | Body |
|---|---|---|---|
| POST | `/register` | Register new user | `name, email, password, avatar` |
| POST | `/login` | Login user | `email, password` |
| POST | `/password/forgot` | Send password reset email | `email` |
| PUT | `/password/reset/:token` | Reset password using token | `password, confirmPassword` |
| GET | `/logout` | Logout current user | — |

### Protected Routes (All Authenticated Users)

| Method | Endpoint | Description | Body |
|---|---|---|---|
| GET | `/me` | Get logged in user profile | — |
| PUT | `/me/update` | Update profile info | `name, email, avatar` |
| PUT | `/password/update` | Change password | `oldPassword, newPassword, confirmPassword` |

### Admin Routes

| Method | Endpoint | Description | Body |
|---|---|---|---|
| GET | `/admin/users` | Get all users | — |
| GET | `/admin/user/:id` | Get single user by ID | — |
| PUT | `/admin/user/:id` | Update user role | `role` |
| DELETE | `/admin/user/:id` | Delete user | — |

### Trainer Routes

| Method | Endpoint | Description | Access |
|---|---|---|---|
| GET | `/trainer/portal` | Get trainer portal data | Trainer, Admin |

---

## Class Routes

### Public Routes

| Method | Endpoint | Description | Query Params |
|---|---|---|---|
| GET | `/classes` | Get all classes | `keyword, category, price[gte], price[lte], ratings[gte], page` |
| GET | `/class/:id` | Get single class details | — |
| GET | `/reviews` | Get all reviews for a class | `id` (class id) |

### Protected Routes (Authenticated Users)

| Method | Endpoint | Description | Body |
|---|---|---|---|
| PUT | `/review` | Create or update a class review | `rating, comment, classId` |
| DELETE | `/reviews` | Delete a review | `id` (review id), `classId` |

### Admin Routes

| Method | Endpoint | Description | Body |
|---|---|---|---|
| GET | `/admin/classes` | Get all classes (admin view) | — |
| POST | `/admin/class/new` | Create new class | `name, description, price, category, capacity, schedule, requiredMembership, trainer, images` |
| PUT | `/admin/class/:id` | Update class | `name, description, price, category, capacity, schedule` |
| DELETE | `/admin/class/:id` | Delete class | — |

---

## Membership Routes

### Protected Routes (Authenticated Users)

| Method | Endpoint | Description | Body |
|---|---|---|---|
| POST | `/membership/new` | Create new membership | `enrolledClasses, healthInfo, membershipType, membershipDuration, itemsPrice, facilityPrice, processingFee, totalPrice, paymentInfo` |
| GET | `/membership/:id` | Get single membership | — |
| GET | `/memberships/me` | Get all memberships of logged in user | — |

### Admin Routes

| Method | Endpoint | Description | Body |
|---|---|---|---|
| GET | `/admin/memberships` | Get all memberships | — |
| PUT | `/admin/membership/:id` | Update membership status | `status` |
| DELETE | `/admin/membership/:id` | Delete membership | — |

---

## Payment Routes

### Protected Routes (Authenticated Users)

| Method | Endpoint | Description | Body |
|---|---|---|---|
| POST | `/payment/process` | Process Stripe payment | `amount` |
| GET | `/stripeapikey` | Get Stripe publishable key | — |

---

## Role Types

| Role | Description | Access Level |
|---|---|---|
| `user` | Regular gym member / trainee | Own profile, browse classes, purchase memberships |
| `trainer` | Gym trainer | Trainer portal, view assigned trainees |
| `admin` | Administrator | Full CRUD on all resources |

---

## Membership Types

| Type | Description |
|---|---|
| `Basic` | Access to basic classes |
| `Standard` | Access to standard and basic classes |
| `Premium` | Access to all classes |

---

## Membership Status Lifecycle

```
Processing → Active → Expired
```

---

## Response Format

All endpoints return responses in this format:

```json
{
  "success": true,
  "message": "Operation successful",
  "data": {}
}
```

## Error Format

```json
{
  "success": false,
  "message": "Error description",
  "statusCode": 400
}
```

---

## Class Categories

`Yoga` | `Cardio` | `Strength Training` | `Zumba` | `CrossFit` | `Pilates` | `Martial Arts` | `Other`

## Fitness Goals

`Weight Loss` | `Muscle Gain` | `Flexibility` | `Endurance` | `General Fitness`

## Experience Levels

`Beginner` | `Intermediate` | `Advanced`
