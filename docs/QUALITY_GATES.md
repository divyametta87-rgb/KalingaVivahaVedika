# Kalinga Vivaha Vedika - Quality Gates & PR Checklist

Every agent-submitted Pull Request must adhere to the following quality checks before being merged into the `develop` or `main` branches.

## 1. Automated Checks (To be configured in CI pipeline)
- [ ] **Build Status**: Code compiles without errors (`mvn clean install` / `npm run build`).
- [ ] **Test Coverage**: All unit and integration tests run successfully.
- [ ] **Linting & Formatting**: Code passes all standard linting rules (ESLint for frontend, Prettier, Checkstyle for backend).
- [ ] **Security Scans**: No high-visibility vulnerabilities reported in dependencies (e.g., via Dependabot or Snyk).

## 2. Agent Output Validation (Before PR Submission)
- [ ] Requirements explicitly fulfilled as per the task definition.
- [ ] No placeholder data or "dummy" links in production-bound files.
- [ ] If making DB schema changes, accompanying migration scripts are provided.
- [ ] Logs and console errors are clean.

## 3. Human Review Requirements
- [ ] Provide a descriptive PR title.
- [ ] Ensure the PR summary includes the "AI Confidence Score" and details decisions that might require human oversight.
- [ ] Review UI components visually to ensure they match the "WOW" factor and rich aesthetics standard before final sign-off.
