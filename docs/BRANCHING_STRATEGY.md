# Agentic Development Branching Strategy

To facilitate autonomous AI agent workflows while maintaining stability and code quality, the "Kalinga Vivaha Vedika" project will adhere to the following branching strategy.

## Key Principles
1. **Isolation**: Agents must work in isolated branches to prevent blocking or breaking the main line of development.
2. **Reviewability**: Human-in-the-loop (HITL) checkpoints should be easy to conduct.
3. **Automated Verification**: Branches must pass strict CI checks (build, lint, test) before merging.

## Branch Types

### 1. `main` branch
- **Purpose**: The single source of truth for production-ready code.
- **Rules**: 
  - Direct commits are forbidden.
  - Changes must come from approved Pull Requests.

### 2. `develop` branch (Optional)
- **Purpose**: Integration branch for accumulating features before a release.
- **Rules**:
  - Agents merge their completed and verified work here.
  - Can be automatically deployed to a staging environment.

### 3. Agent Feature Branches
- **Naming Convention**: `agent/feature/[issue-id]-[brief-description]`
- **Example**: `agent/feature/12-user-authentication`
- **Purpose**: Feature implementation by an AI agent.
- **Workflow**: 
  1. Agent creates branch from `main` or `develop`.
  2. Agent commits iteratively with descriptive, structured commit messages.
  3. Agent opens a PR when the task definition is fully satisfied.

### 4. Agent Bugfix/Hotfix Branches
- **Naming Convention**: `agent/bugfix/[issue-id]-[brief-description]`
- **Purpose**: Isolated branches for agents to fix bugs autonomously.

### 5. Human Intervention Branches
- **Naming Convention**: `human/review-[agent-branch-name]` or `human/fix-[agent-branch-name]`
- **Purpose**: When an agent gets stuck or a PR is rejected, a human engineer can check out the branch, make corrections, and guide the agent back on track.

## AI Agent Git Workflow

1. **Task Assignment**: The agent is assigned a well-defined task.
2. **Branch Creation**: The agent creates a new `agent/*` branch.
3. **Iterative Commits**: The agent commits changes logically, e.g., `feat: add user profile entity` or `test: add unit tests for profile service`.
4. **Validation Checkpoint**: The agent runs tests locally (`npm test`, `mvn test`) before pushing.
5. **Pull Request Initiation**: The agent pushes the branch and creates a PR. The PR description automatically includes a summary of changes, AI confidence score, and specific areas where human review is requested.
6. **Merge**: Once CI passes and human approval (or automated policy approval) is met, the branch is squashed and merged.
