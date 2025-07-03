# Backend Requirement Specifications

This document outlines the technical and functional requirements for core backend features in the Airbnb Clone project.

---

## 1. User Authentication

### 🔹 Feature Summary:
Allow users to register, log in, and manage sessions securely.

### 🔸 API Endpoints:
- `POST /api/register`  
- `POST /api/login`  
- `POST /api/logout`

### 🔸 Inputs:
- Email (string), required, valid email format  
- Password (string), required, minimum 8 characters

### 🔸 Outputs:
- Success: JSON token + user info  
- Error: error message

### 🔸 Validation Rules:
- Email must be unique  
- Passwords must be hashed before storing

### 🔸 Performance Criteria:
- Token generation should take < 500ms  
- Endpoint should support at least 100 concurrent users

---

## 2. Property Management

### 🔹 Feature Summary:
Allow hosts to create, update, view, and delete property listings.

### 🔸 API Endpoints:
- `POST /api/properties`  
- `GET /api/properties/:id`  
- `PUT /api/properties/:id`  
- `DELETE /api/properties/:id`

### 🔸 Inputs:
- Title, Description, Location, Price per night, Photos

### 🔸 Outputs:
- JSON object representing the property

### 🔸 Validation Rules:
- Title must not be empty  
- Price must be a positive number  
- Only authenticated users can manage their own listings

### 🔸 Performance Criteria:
- Property listing retrieval in < 1s  
- File uploads (images) limited to 5MB per image

---

## 3. Booking System

### 🔹 Feature Summary:
Enable users to book available properties for specified dates.

### 🔸 API Endpoints:
- `POST /api/bookings`  
- `GET /api/bookings/:userId`

### 🔸 Inputs:
- Property ID, Start Date, End Date, User ID

### 🔸 Outputs:
- Booking confirmation: Booking ID, dates, amount, status

### 🔸 Validation Rules:
- Dates must not overlap existing bookings  
- User must be authenticated  
- Property must exist and be available

### 🔸 Performance Criteria:
- Booking confirmation in < 1s  
- System should prevent double booking

---

