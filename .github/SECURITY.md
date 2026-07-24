# Security Policy

## Supported Versions

| Version | Supported          |
|---------|--------------------|
| 1.0.x   | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

> [!IMPORTANT]
> Please do **not** report security vulnerabilities through public GitHub issues, discussions, or pull requests.

### Preferred: GitHub Private Vulnerability Reporting

Use the private vulnerability reporting feature built into this repository:

1. Go to https://github.com/alimoradmohameddoweb/valex-os-playbook/security/advisories
2. Click **"New draft security advisory"**
3. Fill in the details (see "What to include" below)

### Fallback: Email

If private vulnerability reporting is unavailable, email the maintainers at `security@valex-os.dev`.

### What to Include

When reporting a vulnerability, please provide:

- The affected version, tag, or commit SHA
- A clear description of the issue and why it is security-sensitive
- Steps to reproduce or a proof of concept
- Any relevant logs, payloads, or screenshots
- The potential impact
- Any suggested mitigations or fixes, if known

### What to Expect

- **Acknowledgment**: You will receive an acknowledgment within **3 business days**
- **Triage**: We will assess the report and follow up with next steps
- **Fix**: If confirmed, we will work on a fix and coordinate disclosure timing with you
- **CVE**: We will publish a GitHub Security Advisory and request a CVE upon release

### Disclosure Policy

We follow **coordinated disclosure** with a 90-day embargo:

- We ask that you keep details private until a fix is released or 90 days elapse
- If 90 days pass without a fix, you may disclose at your discretion
- After release, we publish a GitHub Security Advisory and assign a CVE

## Scope

This security policy covers the Valex OS playbook files (YAML, XML, PowerShell) and the build process. It does **not** cover:

- AME Wizard itself (report to [Ameliorated LLC](https://ameliorated.io))
- Third-party software downloaded by the playbook
- Windows operating system vulnerabilities

## Safe Harbor

We consider security research conducted under this policy as authorized conduct. We will not pursue legal action against researchers who:

- Follow this disclosure policy
- Make a good faith effort to avoid privacy violations, destruction of data, or interruption of services
- Do not exploit a vulnerability beyond what is necessary to confirm its existence
