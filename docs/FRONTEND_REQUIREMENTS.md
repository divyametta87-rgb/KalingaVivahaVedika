# Enterprise Frontend Requirements Document

This document outlines the UI flow, components, and state requirements for the React + Vite frontend of Kalinga Vivaha Vedika, targeting a premium, production-ready user experience.

## 1. App Views (Pages)

### Public Optimization
- **Landing Page (`/`)**: Must achieve 90+ Lighthouse score. Highly optimized images (WebP format). SEO meta tags configured via React Helmet.
- **Onboarding (`/register`)**: Phone Number -> OTP verification flow. Must include a progress bar and high-trust copywriting.

### Private Dashboards (Requires Auth Context)
- **Home/Dashboard**: Infinite scrolling feed. Uses progressive image loading (blurred placeholders transitioning to high-res, similar to Instagram).
- **Search (`/search`)**: Advanced faceted filtering. As choices are made (e.g., selecting a Sub-Caste), the results counter should dynamically update using debounced API calls.
- **Premium Upgrade (`/upgrade`)**: A high-conversion pricing page integrating the Razorpay Checkout UI overlay.
- **Real-time Chat (`/messages`)**: Inbox view with read receipts, typing indicators, and immediate message rendering via WebSockets.

## 2. Global State & Data Fetching
* **Server State Management:** **React Query (TanStack Query)** must be used instead of standard `useEffect` fetches. This provides automatic caching, background refetching, and pagination out of the box.
* **Optimistic UI Updates:** When a user "Likes" a profile, the heart icon must instantly turn red on the frontend *before* the API responds, only reverting if the API call fails.
* **Offline Resilience:** React Query should cache the user's last visited matches so the app doesn't show a blank screen on a subway or spotty cellular connection.

## 3. Core Component Library Requirements
To maintain "WOW" aesthetics, components must feel alive:

* `<BaseButton />`: Must include interactive ripple or scale-down effects on click (using Framer Motion or pure CSS transforms).
* `<Card />`: Glassmorphic UI elements using CSS `backdrop-filter: blur()`.
* `<ImageUploader />`: A drag-and-drop zone that compresses the image purely on the client-side (via a library like `browser-image-compression`) before uploading to S3, saving massive bandwidth costs.

## 4. UI/UX Rules
- **Skeleton Loaders over Spinners:** Never use generic full-screen blocking spinners. Use animated skeleton placeholders for text and images while data fetches.
- **Mobile First Touch Targets:** All interactable elements (buttons, inputs, sliders) must be at least 44x44 pixels to adhere to mobile accessibility standards.
