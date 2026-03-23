# GitHub Copilot App Modernization CLI

Batch assessments across multiple repositories to generate insights, modernization opportunities, and deployment recommendations for Azure services.

## Overview

- Simultaneously assess applications across multiple repos and different languages, either locally or by delegating to a cloud coding agent
- Recommend migration waves based on identified issues and level of effort
- Generate actionable modernization plans and upgrade paths

## When to Use

### CLI

| | Details |
|---|---|
| **Purpose** | Batch assessments, custom modernization plans, and upgrades |
| **Customer Audience** | Application owners and architects |
| **Field Audience** | Solution Engineers |

### IDE (VS Code Extension)

| | Details |
|---|---|
| **Purpose** | Single application assessment, custom modernization plan, upgrade, and deployment |
| **Customer Audience** | Developers |
| **Field Audience** | Cloud Solution Architects |

## Getting Started

### Prerequisites

- [GitHub CLI](https://cli.github.com/) installed
- Authenticated GitHub account

### Authentication

```bash
# Log in to GitHub
gh auth login

# Verify authentication status
gh auth status
```

### Usage

```bash
# Run the modernization agent
modernize
```

### Single Repository

The `modernize` command provides three options for a single project:

1. **Assess Application** — Analyze the application for modernization readiness
2. **Generate Modernization Plan** — Outputs a `plan.md` master file containing:
   - All scenarios similar to the IDE experience in VS Code
   - Designed for Copilot to execute in one-shot
3. **Execute Modernization Plan** — Run the generated plan:
   1. Select the target directory
   2. Select a plan (supports multiple modernization plans)
   3. Execute the plan (optionally provide additional context via prompt, or press Enter to proceed)

### Multi-Repository

Assess multiple repositories in a single batch run.

**Setup:**

1. Navigate to the `.github/modernize/` folder in your repo
2. Create a `repos.json` file listing the repositories to assess:

```json
[
  {
    "name": "Containerization_Assist_App_Mod",
    "url": "https://github.com/oreakinodidi98/Containerization_Assist_App_Mod"
  }
]
```

3. Or if everything is local can put all those source code projects into a repos folder (parent folder)
4. Then can run `modernize -source c:/repos `
5. But if everything is on github can run `modernize` which will scann and identiy x amount of repos in `repos.json`
6. then `CTRL + A` to select all the projects
7. Then can Assess application
   1. Assess locally
      1. Will clone all the repos listed in Github
      2. then go through each source code
      3. loops through all repos
      4. Produces consolidated assessment report
   2. Or delegate to cloud coding agents