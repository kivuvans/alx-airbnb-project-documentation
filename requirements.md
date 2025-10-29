# 🏡 Airbnb Clone Backend – Requirements Specification

**Repository:** `alx-airbnb-project-documentation`  
**File:** `requirements.md`  
**Author:** Evans Kivuva  
**Program:** ALX Software Engineering – Back-End Web Pro-Development  

---

## 📘 Overview
This document defines the **technical** and **functional requirements** for the core backend features of the Airbnb Clone project. The goal is to create a **secure**, **scalable**, and **efficient** backend system that powers property listings, user authentication, and booking management.

---

## 🔑 1. User Authentication and Management

### Functional Description
Enables users to create and manage accounts securely. Users can sign up as **hosts** or **guests**, log in, update profiles, and manage access through authentication tokens.

### API Endpoints
| Method | Endpoint | Description |
|---------|-----------|-------------|
| `POST` | `/api/v1/auth/register` | Register a new user (guest or host) |
| `POST` | `/api/v1/auth/login` | Authenticate a user and return JWT token |
| `GET` | `/api/v1/users/:id` | Retrieve user profile |
| `PUT` | `/api/v1/users/:id` | Update user information |
| `DELETE` | `/api/v1/users/:id` | Deactivate user account |

### Input / Output Specifications
**Input:**
```json
{
  "first_name": "Evans",
  "last_name": "Kivuva",
  "email": "evanskivuva@example.com",
  "password": "SecurePass123!",
  "role": "host"
}
Output:

json
Copy code
{
  "message": "User registered successfully",
  "user_id": "uuid",
  "role": "host",
  "token": "jwt_token"
}
Validation Rules
Email must be unique and valid.

Password must contain at least 8 characters, one uppercase letter, one number, and one special character.

Role must be either guest, host, or admin.

Performance Criteria
Response time: ≤ 200ms for login and registration.

Token expiry: 24 hours.

Maximum login attempts: 5 (with temporary lockout).

🏠 2. Property Management
Functional Description
Allows hosts to manage their listings. Hosts can create, update, or delete property details, including price, description, and availability.

API Endpoints
Method	Endpoint	Description
POST	/api/v1/properties	Add a new property listing
GET	/api/v1/properties	Get all available properties
GET	/api/v1/properties/:id	Retrieve specific property details
PUT	/api/v1/properties/:id	Update property details
DELETE	/api/v1/properties/:id	Remove a property listing

Input / Output Specifications
Input:

json
Copy code
{
  "host_id": "uuid",
  "name": "Cozy Beach Apartment",
  "description": "2-bedroom beachfront property with Wi-Fi and parking.",
  "location": "Mombasa, Kenya",
  "price_per_night": 80.00
}
Output:

json
Copy code
{
  "message": "Property created successfully",
  "property_id": "uuid",
  "status": "active"
}
Validation Rules
name, location, and price_per_night are mandatory.

price_per_night must be greater than 0.

Property cannot be deleted if it has an active booking.

Performance Criteria
Query response ≤ 250ms.

Indexed fields: location, price_per_night, and host_id.

📅 3. Booking System
Functional Description
Facilitates guests to book available properties and manage reservations. Prevents double bookings and tracks booking statuses.

API Endpoints
Method	Endpoint	Description
POST	/api/v1/bookings	Create a new booking
GET	/api/v1/bookings/:id	Retrieve booking details
PUT	/api/v1/bookings/:id/cancel	Cancel an existing booking
GET	/api/v1/bookings/user/:id	View all bookings by user

Input / Output Specifications
Input:

json
Copy code
{
  "user_id": "uuid",
  "property_id": "uuid",
  "start_date": "2025-11-15",
  "end_date": "2025-11-20"
}
Output:

json
Copy code
{
  "message": "Booking confirmed",
  "booking_id": "uuid",
  "status": "confirmed",
  "total_price": 400.00
}
Validation Rules
Booking dates must not overlap with existing bookings for the same property.

Start date must be before end date.

Users cannot book their own property.

Performance Criteria
Must process bookings atomically (ACID compliance).

Response time ≤ 300ms.

Automatic update to property availability after booking.

🧠 Additional Notes
Authentication: Implemented using JWT with refresh tokens.

Database: PostgreSQL (normalized to 3NF).

Logging: All API requests and errors logged via middleware.

Error Handling: Unified error structure using middleware (status, message, details).

✅ Summary of Covered Features
Feature	Key Components	Core Endpoints
User Authentication	Registration, Login, JWT, Roles	/api/v1/auth/*, /api/v1/users/*
Property Management	CRUD Operations, Validation, Indexing	/api/v1/properties/*
Booking System	Booking Logic, Validation, Pricing	/api/v1/bookings/*
