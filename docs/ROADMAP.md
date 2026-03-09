# Project Roadmap: Kalinga Vivaha Vedika

This roadmap defines the development plan for the **Kalinga Vivaha Vedika** platform. It is structured to take full advantage of **Agentic Development**, grouping tasks into well-defined, autonomous chunks that AI coding agents can execute efficiently with minimal human intervention.

## Phase 1: Foundation & Guardrails
**Focus**: Project scaffolding, continuous integration setup, and defining standard operating procedures for AI agents.
* [x] Initialize Git repository
* [x] Setup Frontend (React + Vite)
* [x] Setup Backend (Java + Spring Boot + Maven)
* [ ] **Agent Task**: Establish CI/CD pipelines (GitHub Actions/GitLab CI) to enforce build, test, and style checks on agent PRs.
* [ ] **Agent Task**: Setup database infrastructure (PostgreSQL/MySQL schema orchestration via Flyway/Liquibase).
* [ ] **Agent Task**: Configure strict linting and formatting rules (ESLint, Prettier, Checkstyle) to maintain code consistency across AI outputs.

## Phase 2: Core Platform API (Backend Sprint)
**Focus**: Implementing the business logic, security, and data access layers.
* [ ] **Agent Task**: Implement User Authentication & Authorization (JWT, Spring Security).
* [ ] **Agent Task**: Build CRUD APIs for User Profiles (creating a profile, uploading photos, setting preferences).
* [ ] **Agent Task**: Develop a robust Matchmaking Algorithm API (querying candidates based on caste, education, age, location).
* [ ] **Agent Task**: Implement automated unit and integration testing coverage for all core APIs.

## Phase 3: Core User Experience (Frontend Sprint)
**Focus**: Building a responsive, high-quality "WOW" user interface.
* [ ] **Agent Task**: Construct generic UI components (Buttons, Inputs, Modals, Cards) following a cohesive design system.
* [ ] **Agent Task**: Build the Authentication views (Login, Registration, Password Reset).
* [ ] **Agent Task**: Develop the Dashboard and Profile Management pages.
* [ ] **Agent Task**: Implement the Search & Match results page with interactive filters and smooth micro-animations.

## Phase 4: Enhancements & Communication
**Focus**: Adding features to improve user retention and engagement.
* [ ] **Agent Task**: Implement real-time or near real-time chat/messaging functionality between matched users.
* [ ] **Agent Task**: Setup email/SMS notification dispatchers (e.g., successful registration, new matches).
* [ ] **Agent Task**: Add admin moderation panel (approving profiles, managing reports).

## Phase 5: Polish & Deployment
**Focus**: Preparing for production load and public release.
* [ ] **Agent Task**: Conduct SEO optimization (React Helmet/Meta tags) and performance audits (Lighthouse).
* [ ] **Agent Task**: Containerize the application (Docker) and provide orchestrations scripts (Docker Compose/Kubernetes).
* [ ] Deploy to production infrastructure (AWS/GCP/Azure/Vercel).

---

## 🤖 Continuous Agent Handoffs & Milestones
To maintain velocity without losing control, the project will observe these milestones:
1. **MVP Checkpoint (End of Phase 3):** Human review of the entire end-to-end matching flow before adding Enhancements (Phase 4).
2. **Weekly PR Audits:** Human maintainer reviews the `PROJECT_TRACKER.md` to prune stale tasks or adjust priority of the agent backlog.
3. **Architecture Reviews:** Before adding any new major third-party dependencies not listed in `ARCHITECTURE.md`, an explicit architecture review issue must be opened by the AI agent.
