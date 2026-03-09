# AI Agent Guidelines & Standard Operating Procedures

To ensure a smooth, stable, and high-quality development process, all AI agents contributing to the **Kalinga Vivaha Vedika** project must strictly adhere to these guidelines.

## 1. File Modification Rules
- **Do NOT hallucinate paths**: Always use tools (`ls`, `find`) to verify file locations before editing.
- **Minimal Edits**: Only modify the lines necessary for the task. Avoid reformatting entire files unless explicitly requested.
- **Dependencies**: Do not add new third-party libraries (npm packages or Maven dependencies) without logging the justification in the PR.

## 2. Commit Standards
- Follow Conventional Commits format: `type(scope): description`.
- **Types**: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.
- Provide meaningful context if the commit involves complex logic.

## 3. The "WOW" UI Standard
- For frontend tasks, UI aesthetics are paramount. 
- Ensure proper use of CSS variables (colors, spacing).
- Implement responsive design (mobile-first).
- Incorporate subtle micro-animations (hover states, transitions) to make the app feel alive.

## 4. Stuck State / Infinite Loops
- If you (the agent) fail to resolve a test error or lint issue after 3 attempts, **STOP**.
- Commit the current state to the feature branch.
- Document the exact error and steps already taken in the PR or a `tmp/error_log.txt` file.
- Hand execution back to the user or human engineer for guidance.
