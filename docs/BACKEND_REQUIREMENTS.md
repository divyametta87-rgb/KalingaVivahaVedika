# Backend Requirements Document

This document defines the core backend requirements for the Kalinga Vivaha Vedika application. It must be implemented using **Java 17+** and **Spring Boot 3**.

## 1. Database Schema Models (Entities)

### `User` (Authentication)
* `id` (UUID, Primary Key)
* `email` (String, Unique, Not Null)
* `passwordHash` (String, Not Null)
* `role` (Enum: USER, ADMIN)
* `createdAt` (Timestamp)
* `status` (Enum: ACTIVE, PENDING_VERIFICATION, SUSPENDED)

### `Profile` (Matchmaking Data)
* `id` (UUID, Primary Key)
* `userId` (UUID, Foreign Key to User, One-to-One)
* `firstName` (String)
* `lastName` (String)
* `gender` (Enum: MALE, FEMALE)
* `dateOfBirth` (Date)
* `maritalStatus` (Enum: NEVER_MARRIED, DIVORCED, WIDOWED)
* `heightCm` (Integer)
* `education` (String)
* `profession` (String)
* `subCaste` (String - Specific to Kalinga community distinctions)
* `city` (String)
* `state` (String)
* `country` (String)
* `aboutMe` (Text)
* `photoUrls` (Array of Strings / JSON column)

### `Preference` (Partner Let Look)
* `id` (UUID, Primary Key)
* `profileId` (UUID, Foreign Key)
* `minAge` (Integer)
* `maxAge` (Integer)
* `minHeightCm` (Integer)
* `educationReq` (List of Strings)
* `maritalStatusReq` (List of Enums)

## 2. Core REST APIs (v1)

### Authentication (`/api/v1/auth`)
* `POST /register`: Accepts email/password, creates `User`, returns JWT.
* `POST /login`: Authenticates credentials, returns JWT.
* `POST /refresh`: Refresh an expired JWT.

### Profiles (`/api/v1/profiles`)
* `GET /me`: Returns the logged-in user's profile.
* `POST /` : Create initial profile setup.
* `PUT /{id}`: Update profile details.
* `POST /{id}/photos`: Upload profile pictures.

### Matchmaking (`/api/v1/matches`)
* `GET /recommendations`: Main matching algorithm endpoint. Returns a paginated list of `Profile` objects that score highly against the user's `Preference` criteria, prioritizing exact sub-caste or location matches based on complex business logic.

## 3. Security Requirements
* All endpoints (except `/auth/*`) must be secured via **Spring Security** using Stateless JWT authentication.
* Passwords must be hashed using BCrypt.
* CORS must be strictly configured to allow only the production/staging Vite frontend URLs.
