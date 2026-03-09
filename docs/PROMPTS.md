# AI Agent Prompt Library

This folder curates highly effective prompt templates for instructing AI coding agents on this specific repository.

## 1. Starting a New Backend Feature
Copy and paste this when asking the AI to build a new API:

> "Please transition to the `backend/` directory. Your goal is to implement the **[FEATURE_NAME]** functionality. 
> 
> Review `docs/ARCHITECTURE.md` for context on the Spring Boot stack. 
> 1. Start by creating the JPA Entity.
> 2. Create the Repository interface.
> 3. Implement the Service layer with business logic.
> 4. Create the REST Controller.
> 
> Write thorough JUnit/Mockito tests for the Service layer. Do not proceed to the Controller until the service tests pass. Commit your work to a new `agent/feature/[name]` branch."

## 2. Generating a Frontend Component
Copy and paste this when asking the AI to build a new UI component:

> "Please transition to the `frontend/` directory. Your goal is to build a new **[COMPONENT_NAME]** component.
>
> Review `docs/USER_PERSONA.md` first. Ensure the design is mobile-first, highly accessible, and uses our established CSS variables for theming. Add subtle hover animations to make it feel premium. 
> 
> Create the `.jsx` file and a corresponding `.css` file if specific styling is needed. Hook the component into the main `App.jsx` layout for visual verification, and confirm there are no ESLint warnings before committing."

## 3. Debugging / Stuck State
If the AI is failing to compile or failing tests:

> "I notice you are getting stuck on the [TEST/BUILD] error. Stop trying to write new logic.
> 
> 1. Read the exact stack trace again.
> 2. Check the project dependencies in `pom.xml` or `package.json` to ensure versions aren't colliding.
> 3. Use `grep` to look for similar working patterns elsewhere in the codebase.
> 
> Write your hypotheses into `docs/tmp/debug_log.md` and present me with 2 possible paths forward before making any further code changes."
