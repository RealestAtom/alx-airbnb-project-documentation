# Airbnb Clone – Backend Feature Requirements

## 🧠 Overview

This document outlines the **technical** and **functional** requirements for the key backend features of the Airbnb Clone project.  
The backend is built to support user authentication, property management, and booking operations while ensuring scalability, security, and reliability.

---

## 1️⃣ User Authentication

### 🧩 Functional Requirements
- Users can register as guests or hosts.
- Users can log in with email and password.
- Passwords must be securely hashed.
- The system must issue JSON Web Tokens (JWT) for authentication.
- Sessions should expire after a set duration (e.g., 1 hour).

### ⚙️ API Endpoints
| Method | Endpoint | Description |
|---------|-----------|-------------|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Authenticate user and return JWT |
| `GET`  | `/api/auth/profile` | Retrieve logged-in user’s profile |
| `PUT`  | `/api/auth/profile` | Update user information |

### 🧾 Input & Output Examples

**Register (POST /api/auth/register)**  
```json
Input:
{
  "first_name": "Evans",
  "last_name": "Adongo",
  "email": "evans@example.com",
  "password": "securePass123",
  "role": "host"
}

Output:
{
  "message": "User registered successfully",
  "token": "<jwt_token>",
  "user": {
    "id": 1,
    "first_name": "Evans",
    "role": "host"
  }
}
### To add property
Input:
{
  "title": "Modern Beachfront Apartment",
  "description": "2-bedroom apartment with ocean view",
  "price": 150.0,
  "location": "Cape Coast, Ghana",
  "amenities": ["WiFi", "Air Conditioning", "Parking"]
}

Output:
{
  "message": "Property added successfully",
  "property_id": 101
}
### To create booking
Input:
{
  "property_id": 101,
  "user_id": 1,
  "start_date": "2025-11-01",
  "end_date": "2025-11-05"
}

Output:
{
  "message": "Booking created successfully",
  "booking_id": 50,
  "status": "confirmed"
}
