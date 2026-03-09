# Frontend Requirements Document

This document outlines the UI flow, components, and state requirements for the React + Vite frontend of Kalinga Vivaha Vedika.

## 1. App Views (Pages)

### Public Security Views
- **Landing Page (`/`)**: High-impact hero section highlighting trust, community, and success stories. Call to action to Register or Login.
- **Login (`/login`)**: Email/Password form.
- **Registration (`/register`)**: Multi-step wizard to capture base authentication, then initial profile details to prevent drop-off.

### Private Dashboards (Requires Auth Context)
- **Home/Dashboard (`/dashboard`)**: The main feed. Displays "Today's Top Matches" tailored by the backend algorithm.
- **My Profile (`/profile`)**: Extensive form to edit personal details, upload photos, and modify partner preferences. Must show a "Profile Completeness" progress bar.
- **Search (`/search`)**: Advanced filtering view. Users can manually refine matches by age, sub-caste, education, and location.
- **Matches/Interests (`/interests`)**: Shows profiles the user has "Liked" or received "Likes" from.

## 2. Global State Management (React Context)
* **AuthContext**: Manages the JWT token, current `userId`, and `role`. Handles auto-logout on token expiration.
* **NotificationContext**: A global toast manager for success messages (e.g., "Profile Updated") and error handling (e.g., "Network Error").

## 3. Core Component Library Requirements
To maintain "WOW" aesthetics and consistency, agents must build these reusable foundational components before building complex views:

* `<BaseButton />`: Variants for Primary (Deep Red/Gold), Secondary (Outline), and Ghost. Must include unified `disabled` and `loading` states (with micro-spinners).
* `<Card />`: Glassmorphic or softly shadowed containers for Profile previews. Needs a clean hover animation (slight lift or border glow).
* `<FormInput />`, `<FormSelect />`, `<FormDatepicker />`: Reusable controlled inputs with unified error label styling.
* `<Modal />`: An animated overlay component for things like "Confirm Interest" or "Viewing Full Image".

## 4. UI/UX Rules
- **No Empty States**: If `/interests` is empty, show a high-quality SVG illustration with text like "No connections yet. Keep exploring your matches!"
- **Responsive Layout**: The `Navbar` must collapse into a Hamburger menu on mobile. The `Dashboard` grid should shift from 3 columns (Desktop) to 1 column (Mobile).
