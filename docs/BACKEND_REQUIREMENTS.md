# Enterprise Backend Requirements Document

This document defines the core backend requirements for the Kalinga Vivaha Vedika application, architected for scale (1,000 to 10,000+ users). It must be implemented using **Java 17+** and **Spring Boot 3**.

## 1. Database Schema Models (Entities)

### `User` & Security
* `id` (UUID, Primary Key)
* `phone` (String, Unique, Not Null) - *Primary login mechanism via OTP*
* `email` (String, Unique)
* `role` (Enum: USER, PREMIUM_USER, ADMIN)
* `status` (Enum: ACTIVE, PENDING_VERIFICATION, SUSPENDED)
* `subscriptionEndDate` (Timestamp)

### `Profile` (Matchmaking Data)
* `id` (UUID, Primary Key)
* `userId` (UUID, Foreign Key mapping)
* `firstName`, `lastName`, `gender`, `dateOfBirth`
* `heightCm`, `education`, `profession`, `incomeRange`
* `subCaste`, `gotra`, `city`, `state`, `country`
* `aboutMe` (Text)
* `photoUrls` (Array of Strings mapping to AWS S3/Cloudinary URLs)
* `isVerified` (Boolean - Approved by Admin moderation)

### `Preference` (Partner Look)
* `id`, `profileId`, `minAge`, `maxAge`, `minHeightCm`
* `educationReq`, `maritalStatusReq`, `subCasteReq`

### `Subscription` (Monetization)
* `id`, `userId`, `planType` (Enum: FREE, GOLD, PLATINUM)
* `razorpayOrderId`, `razorpayPaymentId`, `status`
* `amount`, `startDate`, `endDate`

## 2. Advanced Core APIs (v1)

### Authentication & Security (`/api/v1/auth`)
* `POST /send-otp`: Integrates with Twilio/Msg91.
* `POST /verify-otp`: Validates OTP and returns JWT.

### Profiles & Media (`/api/v1/profiles`)
* `POST /{id}/photos/presigned-url`: Returns an AWS S3 pre-signed URL so the frontend can upload images directly to the cloud, saving server bandwidth.

### Enterprise Matchmaking & Search (`/api/v1/matches`)
* `GET /feed`: Uses **Redis** caching to serve the daily feed of profiles instantly.
* `POST /search`: Complex, multi-faceted filtering. *Future state: Migrate this query to **ElasticSearch** for fuzzy matching and weighted scoring.*

### Communication & WebSockets (`/ws/chat`)
* Implementing Spring Boot WebSockets with STOMP protocol.
* Users can only message each other if both have "Mutual Likes" or if the sender is a `PREMIUM_USER`.

### Monetization (`/api/v1/payments`)
* `POST /create-order`: Generates a Razorpay Order ID.
* `POST /webhook/razorpay`: Listens for successful payment events to upgrade user roles.
