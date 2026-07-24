# Contributing to Valex OS

First off, thank you for considering contributing to Valex OS. It is people like you who make this project what it is.

> [!NOTE]
> This document is the single source of truth for how to contribute. Reading it before opening your first issue or pull request will save everyone time.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Improving Documentation](#improving-documentation)
  - [Submitting Changes](#submitting-changes)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Commit Messages](#commit-messages)
- [Pull Request Process](#pull-request-process)
- [Getting Help](#getting-help)

---

## Code of Conduct

This project and everyone participating in it is governed by the [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to `conduct@valex-os.dev`.

---

## Getting Started

Valex OS is an [AME Wizard](https://ameliorated.io) playbook. The project uses:

- **YAML** for all playbook actions (12 task files under `Configuration/Tasks/`)
- **XML** for `playbook.conf` (playbook descriptor)
- **PowerShell** for `build.ps1` (archive builder)
- **GitHub Actions** for CI/CD (`.github/workflows/`)

### Prerequisites

- Windows 10/11 (for local build testing)
- [7-Zip](https://7-Zip.org) installed (or auto-downloaded by build script)
- Basic familiarity with [AME Wizard YAML actions](https://docs.amelabs.net)

---

## How to Contribute

### Reporting Bugs

> [!IMPORTANT]
> Please use the [Bug Report](https://github.com/alimoradmohameddoweb/valex-os-playbook/issues/new/choose) template — it guides you through the information we need.

A good bug report includes:

- The Windows build number you applied the playbook to
- The version of Valex OS and AME Wizard used
- Clear steps to reproduce the issue
- What you expected to happen vs. what actually happened
- Relevant log output from AME Wizard (click "Open Logs Folder")

### Suggesting Enhancements

> [!TIP]
> Use the [Feature Request](https://github.com/alimoradmohameddoweb/valex-os-playbook/issues/new/choose) template.

When suggesting an enhancement, focus on **the problem you are solving**, not just the solution you have in mind. This helps us evaluate alternatives and find the best approach.

### Improving Documentation

Documentation improvements are always welcome. Use the [Documentation](https://github.com/alimoradmohameddoweb/valex-os-playbook/issues/new/choose) template and be specific about what is unclear or missing.

### Submitting Changes

> [!WARNING]
> For significant changes, open a discussion first. Spending a week implementing something that does not align with the project direction helps no one.

---

## Development Setup

```powershell
# Clone the repository
git clone https://github.com/alimoradmohameddoweb/valex-os-playbook.git
cd valex-os-playbook

# Build the .apbx archive
.\build.ps1

# The built file will be Valex-OS.apbx in the current directory
```

No additional dependencies are required. The build script auto-detects or downloads 7-Zip.

### Project Structure

```
valex-os-playbook/
├── playbook.conf              # AME Wizard configuration (XML)
├── build.ps1                  # Archive builder
├── Images/                    # OOBE software icons (128px PNG)
├── Configuration/
│   ├── main.yml               # Entry point — 11 phases
│   └── Tasks/
│       ├── privacy.yml        # Telemetry elimination (~237 actions)
│       ├── debloat.yml        # AppX/capability removal (~115 actions)
│       ├── services.yml       # Service optimization (~81 actions)
│       ├── performance.yml    # CPU/GPU/memory/timer tuning (~120 actions)
│       ├── network.yml        # TCP/IP/DNS optimization (~41 actions)
│       ├── security.yml       # TLS/SMB/cipher hardening (~145 actions)
│       ├── updates.yml        # Windows Update policy (~48 actions)
│       ├── interface.yml      # Shell/taskbar/explorer cleanup (~195 actions)
│       ├── cleanup.yml        # Scheduled tasks/file cleanup (~62 actions)
│       ├── software.yml       # Browser/tools installation (~66 actions)
│       └── finalize.yml       # Branding, wallpaper, final tuning (~50 actions)
└── Executables/
    └── Media/                 # Wallpaper + lock screen images
```

---

## Coding Standards

### YAML

- Use 2-space indentation
- Use the YAML `---` document separator at the top of every file
- Keep `!action:` tags on their own line for readability
- Use single quotes for string values when the value contains special characters
- Comment every section with a clear header comment
- Document *why* a change is made, not just *what* it does — especially for registry values

Example:
```yaml
# Disable legacy protocol to reduce attack surface
- !registryValue:
  path: 'HKLM\SYSTEM\...'
  value: 'Enabled'
  type: REG_DWORD
  data: '0'
  option: some-feature
  builds: ['>=22000']
```

### PowerShell (build.ps1)

- Follow existing script conventions (parameter blocks, sections, error handling)
- Use `$ErrorActionPreference = "Stop"` and `Set-StrictMode -Version Latest`
- Comment every major block

### Actions

- Every `!service` deletion should include `iso: true, oobe: false` to enable ISO injection compatibility
- Use `option:` for feature gating, not `if:` conditionals
- Use `errorAction: log` for non-critical operations
- Use `builds:` with version ranges for Win11-only actions
- Use `type: family` on all `!appx` actions

---

## Commit Messages

We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>: <short description>

[optional body explaining what and why, not how]
```

### Types

| Type     | Usage                                         |
|----------|-----------------------------------------------|
| `feat`   | A new feature or enhancement                  |
| `fix`    | A bug fix                                     |
| `docs`   | Documentation only changes                    |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `perf`   | A performance optimization                    |
| `test`   | Adding or correcting tests                    |
| `chore`  | Build, CI, dependencies, tooling              |

### Commit Body Guidelines

- Explain **what** changed and **why**, not **how**
- Reference issues with `Closes #123` or `Refs #456`
- Sign off your commits with `git commit -s` (adds `Signed-off-by` trailer — this is a [Developer Certificate of Origin](https://developercertificate.org/))

Example:
```
feat: disable Windows Recall via additional policy paths

Windows Recall persists AI screenshot captures even when the primary
registry value is set. This commit adds secondary policy paths and
IFEO process killers to ensure Recall cannot activate.

Closes #42
Signed-off-by: Your Name <your.email@example.com>
```

---

## Pull Request Process

### Before Submitting

1. [ ] Have you opened a discussion or identified an issue for significant work?
2. [ ] Is your branch based on `main` and up to date?
3. [ ] Have you followed the coding standards above?
4. [ ] Have you verified that `.\build.ps1` completes successfully?
5. [ ] Have you tested your changes on a fresh Windows installation (or ISO injection)?
6. [ ] Have you used `git commit -s` to sign off?

### When Opening

1. Title your PR using [Conventional Commits](https://www.conventionalcommits.org/) format
2. Fill out the [pull request template](.github/PULL_REQUEST_TEMPLATE.md) completely
3. Open work-in-progress PRs as **drafts**
4. Link the relevant issue with `Closes #000`

### After Opening

- Keep your branch up to date with `main` via `git rebase`
- If changes are requested, amend existing commits rather than adding new ones
- Use `git push --force-with-lease` (safer than `--force`)
- Respond to review comments promptly

### Review Criteria

Pull requests are evaluated on:

- **Correctness**: Does the change do what it claims?
- **Safety**: Could this break a user's system? Are there adequate safeguards (build guards, feature gates, error handling)?
- **Maintainability**: Is the code well-commented and consistent with existing patterns?
- **Completeness**: Are documentation and changelog entries included where appropriate?

---

## Getting Help

- **Discussions**: Use [GitHub Discussions](https://github.com/alimoradmohameddoweb/valex-os-playbook/discussions) for questions
- **AME Docs**: [docs.amelabs.net](https://docs.amelabs.net) — official AME Wizard documentation
- **Support**: See [SUPPORT.md](SUPPORT.md) for more resources

---

*Thank you for contributing to Valex OS!*
