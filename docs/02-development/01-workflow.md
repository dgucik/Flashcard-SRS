# Git Workflow & Standards

This document outlines the branching strategy, pull request process, and commit conventions used in this project. We follow a strict **Squash & Merge** workflow to maintain a linear and clean history on the `master` branch.

---

## 1. Branching Strategy

We use short-lived branches created directly from `master`. Do not commit directly to `master`.

### Branch Naming Convention
Branches must follow the format: `type/kebab-case-description`

| Type | Description | Example Branch Name |
| :--- | :--- | :--- |
| **feat** | New feature implementation | `feat/user-login-flow` |
| **fix** | Bug fix | `fix/prevent-crash-on-safari` |
| **docs** | Documentation changes | `docs/add-core-business-context` |
| **refactor** | Code restructuring (no logic change) | `refactor/clean-up-user-service` |
| **chore** | Configuration/Build tasks | `chore/update-dependencies` |
| **release** | Release preparation | `release/0.1.0` |

---

## 2. Development Lifecycle

### Step 1: Create a Branch
Always checkout from the latest `master`:
```bash
git checkout master
git pull origin master
git checkout -b docs/add-core-business-context-and-definitions
```

### Step 2: Work & Commit
While working on your branch, commit as often as needed. These intermediate commits will be squashed later.

### Step 3: Open Pull Request (PR)
When the work is ready:
1. Push the branch to the repository.
2. Open a Pull Request against **`main`**.
3. Wait for **CI Checks** to pass (green status).
4. Request Code Review (approval is required).

### Step 4: Squash & Merge
Once approved and CI passes:
1. Use the **Squash and Merge** option.
2. **Crucial:** Edit the final commit message to follow the **Commit Convention** (see Section 3 below).
3. Merge.
4. **Delete** the source branch immediately after merging.

---

## 3. Commit Convention (Main History)

The final commit message (applied during "Squash & Merge") must follow the Conventional Commits format, using only the **Type** and the **Imperative Verb** in the description:

`type: Imperative verb + description`

### Rules
1. **Type:** Must be one of the types listed in Section 1 (e.g., `feat`, `fix`, `docs`).
2. **Imperative Verb:** The description **must** start with one of the allowed verbs below.
3. **No Period:** Do not end the subject line with a period.

### Allowed Imperative Verbs
Start your description with one of these:

* **Add** - Add a new capability, file, or feature.
* **Create** - Create a new resource or artifact.
* **Update** - Update existing code, libraries, or logic.
* **Refactor** - Restructure code without changing behavior.
* **Rename** - Rename files or variables.
* **Set up** - Configure infrastructure or tools.
* **Delete** - Remove files or code.

### ✅ Examples
* `docs: Add core business context and definitions`
* `feat: Create user registration endpoint`
* `fix: Update validation logic for emails`
* `chore: Set up initial CI pipeline`

---

## 4. Release Strategy

We use Semantic Versioning (SemVer) for versioning. Release branches are used to tag a specific state of the project.

### Branch Name
Format: `release/X.Y.Z` (e.g., `release/0.1.0`)

### Versioning Rules (SemVer)
Given a version number **MAJOR.MINOR.PATCH**:

1.  **MAJOR** (e.g., `1.0.0` → `2.0.0`)
    * When you make **incompatible API changes** (Breaking Changes).
2.  **MINOR** (e.g., `0.1.0` → `0.2.0`)
    * When you add **functionality** in a backward-compatible manner (Features).
3.  **PATCH** (e.g., `0.1.0` → `0.1.1`)
    * When you make backward-compatible **bug fixes** (Bug Fixes).

### Release Process
1.  Create a branch `release/X.Y.Z` from **`main`**.
2.  Bump version numbers in package files (e.g., `package.json`).
3.  Generate or update the CHANGELOG based on recent commits.
4.  Merge to **`main`** (usually using Squash & Merge).
5.  Create a Git Tag (e.g., `v0.1.0`) on **`main`**.