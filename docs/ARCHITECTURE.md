# Project Architecture & Technology Stack

**Kalinga Vivaha Vedika** is a modern, full-stack matchmaking web application. This document serves as the foundational architectural context for all AI agents working on the repository.

## 🧱 The Technology Stack

### 1. Frontend (Client-Side)
- **Framework:** React 18+ (using Vite for blazing fast builds)
- **Styling:** Vanilla CSS (`index.css` and `App.css`) with CSS variables. *No TailwindCSS unless explicitly requested later.*
- **Routing:** React Router DOM (To be implemented)
- **State Management:** React Context API / Custom Hooks

### 2. Backend (Server-Side)
- **Language:** Java 17+
- **Framework:** Spring Boot 3+ (Spring Web, Spring Data JPA, Spring Security)
- **Build Tool:** Maven

### 3. Database (Persistence Layer)
- **Database Engine:** PostgreSQL (Ideal) or MySQL. *Agents should default to PostgreSQL syntax.*
- **Object Relational Mapping (ORM):** Hibernate (via Spring Data JPA)
- **Migrations:** Flyway or Liquibase (To be integrated)

## 📂 Project Structure Walkthrough

```
/
├── backend/          # Spring Boot Application Root
│   ├── src/          # Java source code
│   └── pom.xml       # Maven dependencies
├── frontend/         # React Application Root
│   ├── src/          # React components, pages, styles
│   └── package.json  # NPM dependencies
└── docs/             # Project guidelines, roadmaps, tracking
    └── tmp/          # AI Agent local scratchpad (gitignored)
```

## 🔐 Core Data Entities (Draft)
When building APIs or UI forms, agents should assume the following core entities exist or will be required:
1. **User:** Base authentication details (Email, Password Hash, Role).
2. **Profile:** Matchmaking details (Name, Age, Caste, Education, Photos, Preferences).
3. **Matches:** Records of user connections/interests.
