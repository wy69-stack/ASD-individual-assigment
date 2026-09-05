# Database Design - PawBuddy (PetCare Connect)

This document outlines the database schema for the PawBuddy MVP system.

---

## 1. Database Schema Overview

The database consists of 4 primary tables to manage users, provider profiles, pet care services, and booking transactions:

### Table 1: `users`
Stores account details for both pet owners and caregivers.

| Field Name | Data Type | Key / Constraints | Description |
| :--- | :--- | :--- | :--- |
| `user_id` | INT | PRIMARY KEY, AUTO_INCREMENT | Unique identifier for each user |
| `full_name` | VARCHAR(100) | NOT NULL | User's full name |
| `email` | VARCHAR(100) | UNIQUE, NOT NULL | Account email address |
| `password_hash`| VARCHAR(255) | NOT NULL | Encrypted password |
| `phone_number` | VARCHAR(20) | NULL | Contact phone number |
| `role` | ENUM | 'owner', 'provider' | Account role |
| `created_at` | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | Account creation date |

---

### Table 2: `provider_profiles`
Stores additional profile details specific to pet care providers.

| Field Name | Data Type | Key / Constraints | Description |
| :--- | :--- | :--- | :--- |
| `provider_id` | INT | PRIMARY KEY, AUTO_INCREMENT | Unique provider ID |
| `user_id` | INT | FOREIGN KEY (`users.user_id`) | Links to main user account |
| `location_area`| VARCHAR(150) | NOT NULL | General service location/city |
| `experience_years`| INT | DEFAULT 0 | Years of pet care experience |
| `bio_description`| TEXT | NULL | Profile summary/bio |
| `hourly_rate` | DECIMAL(10, 2)| NOT NULL | Service price rate |

---

### Table 3: `services`
Defines available pet care service categories.

| Field Name | Data Type | Key / Constraints | Description |
| :--- | :--- | :--- | :--- |
| `service_id` | INT | PRIMARY KEY, AUTO_INCREMENT | Unique service ID |
| `service_name` | VARCHAR(50) | NOT NULL | Service type (Dog Walking, Sitting, etc.) |

---

### Table 4: `bookings`
Stores booking requests submitted by pet owners to providers.

| Field Name | Data Type | Key / Constraints | Description |
| :--- | :--- | :--- | :--- |
| `booking_id` | INT | PRIMARY KEY, AUTO_INCREMENT | Unique booking request ID |
| `owner_id` | INT | FOREIGN KEY (`users.user_id`) | Pet owner requesting the service |
| `provider_id` | INT | FOREIGN KEY (`provider_profiles.provider_id`) | Selected care provider |
| `service_id` | INT | FOREIGN KEY (`services.service_id`) | Selected service category |
| `booking_date` | DATE | NOT NULL | Date of service |
| `start_time` | TIME | NOT NULL | Requested start time |
| `status` | ENUM | 'Pending', 'Confirmed', 'Cancelled' | Booking state |