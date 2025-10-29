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

**Output:**
{
  "message": "User registered successfully",
  "user_id": "uuid",
  "role": "host",
  "token": "jwt_token"
}

