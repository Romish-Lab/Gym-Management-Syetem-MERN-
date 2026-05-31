# API Documentation

Base URL: `http://localhost:8000/api/v1`

---

## Auth Routes `/api/v1/auth`

| Method | Endpoint                  | Description            | Access    | Body                                               |
| ------ | ------------------------- | ---------------------- | --------- | -------------------------------------------------- |
| POST   | `/register`               | Register new user      | Public    | `full_name, email, password, phone, profile_image` |
| POST   | `/login`                  | Login user             | Public    | `email, password`                                  |
| DELETE | `/delete/:id`             | Delete user            | Admin     | -                                                  |
| PUT    | `/update/:id`             | Update user            | Admin     | `full_name, phone, profile_image`                  |
| GET    | `/profile/:id`            | Get user profile       | All roles | -                                                  |
| POST   | `/change-password`        | Change password        | All roles | `currentPassword, newPassword`                     |
| PUT    | `/change-profile-picture` | Update profile picture | All roles | `profile_image`                                    |

---

## Brand Routes `/api/v1/brands`

| Method | Endpoint | Description     | Access | Body               |
| ------ | -------- | --------------- | ------ | ------------------ |
| GET    | `/`      | Get all brands  | Public | -                  |
| GET    | `/:id`   | Get brand by ID | Public | -                  |
| POST   | `/`      | Create brand    | Admin  | `name, brand_logo` |
| PUT    | `/:id`   | Update brand    | Admin  | `name, brand_logo` |
| DELETE | `/:id`   | Delete brand    | Admin  | -                  |

---

## Category Routes `/api/v1/categories`

| Method | Endpoint | Description        | Access | Body                  |
| ------ | -------- | ------------------ | ------ | --------------------- |
| GET    | `/`      | Get all categories | Public | -                     |
| GET    | `/:id`   | Get category by ID | Public | -                     |
| POST   | `/`      | Create category    | Admin  | `name, category_logo` |
| PUT    | `/:id`   | Update category    | Admin  | `name, category_logo` |
| DELETE | `/:id`   | Delete category    | Admin  | -                     |

---

## Product Routes `/api/v1/products`

| Method | Endpoint                | Description              | Access | Body                                                                    |
| ------ | ----------------------- | ------------------------ | ------ | ----------------------------------------------------------------------- |
| GET    | `/`                     | Get all products         | Public | -                                                                       |
| GET    | `/:id`                  | Get product by ID        | Public | -                                                                       |
| GET    | `/featured`             | Get featured products    | Public | -                                                                       |
| GET    | `/new-arrivals`         | Get new arrivals         | Public | -                                                                       |
| GET    | `/category/:categoryId` | Get products by category | Public | -                                                                       |
| POST   | `/`                     | Create product           | Admin  | `name, description, price, stock, category, brand, cover_image, images` |
| PUT    | `/:id`                  | Update product           | Admin  | `name, description, price, stock`                                       |
| DELETE | `/:id`                  | Delete product           | Admin  | -                                                                       |

---

## Role Types

| Role          | Access Level                            |
| ------------- | --------------------------------------- |
| `USER`        | Own profile, browse, purchase           |
| `ADMIN`       | Full CRUD on all resources              |
| `SUPER_ADMIN` | All admin permissions + user management |

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

## Authentication

All protected routes require a valid JWT token stored in an `access_token` cookie, set automatically on login or registration.
