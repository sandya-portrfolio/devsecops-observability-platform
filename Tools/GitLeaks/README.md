
# Preparing the Secret Management & Zero Trust Implementation as a GitHub Project

## 1. Project Overview

### Purpose
This project demonstrates practical usage of two powerful industry tools:
- **GitLeaks**: To detect accidental secret leaks in Git repositories.
- **HashiCorp Vault**: To securely store secrets and implement zero trust principles.

It builds upon theoretical concepts of Secret Management and Zero Trust Mindset by applying them practically—detecting leaked secrets, rotating keys securely, and applying least privilege access policies.

---

## 2. Project Structure

Organize your GitHub repository with the following folder and file structure:

```
/gitleaks-vault-project
│
├── README.md
├── .gitignore
├── scripts/
│   ├── install_gitleaks.sh
│   ├── install_vault.sh
│   ├── detect_leaks.sh
│   ├── vault_setup.sh
│   └── rotate_secrets.sh
├── config/
│   ├── example_secret_config.env
│   ├── secret_policy.hcl
│   └── vault_ignore_file.gitleaksignore
├── src/
│   └── sample_code.py
└── docs/
    └── usage_guide.md
```

---

## 3. Detailed Breakdown of Components

### a) README.md
- Explain the project purpose.
- Include prerequisites (Git, Vault, GitLeaks, sudo access).
- Provide step-by-step instructions to run each script.
- Highlight important commands and concepts (secret detection, rotation, least privilege).

### b) scripts/

- **install_gitleaks.sh**  
  Shell script for downloading and installing GitLeaks on local system:
  - Download zip file.
  - Unzip and move binary to `/usr/local/bin`.
  - Use `sudo` as needed.

- **install_vault.sh**  
  Script to install Vault via Snap or other package managers.

- **detect_leaks.sh**  
  Script to:
  - Initialize a test Git repo.
  - Commit a file with a secret (example AWS API key).
  - Run `gitleaks detect --source . -v` to scan the repo.
  - Output detected leaks with details (file, line, secret).

- **vault_setup.sh**  
  Script to:
  - Start Vault development server.
  - Export Vault address and root token as environment variables.
  - Enable KV-v2 secrets engine at a specified path.
  - Create and apply a Vault policy following least privilege principle.
  - Create a token with restricted permissions.

- **rotate_secrets.sh**  
  Script demonstrating:
  - Securely storing secrets in Vault instead of hardcoding.
  - Rotating (revoking old keys, generating new ones).
  - Fetching secrets dynamically in code.

### c) config/

- **example_secret_config.env**  
  Example config file with hardcoded secrets (for demo purposes only, marked unsafe).

- **secret_policy.hcl**  
  Vault policy file to restrict access to secrets:
  - Allow read-only permissions on secrets path.
  - Deny delete or write operations.
  - Illustrates least privilege access.

- **vault_ignore_file.gitleaksignore**  
  A file containing fingerprints of known leaks to ignore in GitLeaks scans.

### d) src/sample_code.py

- Python example demonstrating:
  - Importing `os` module.
  - Fetching secrets from environment variables that map to Vault.
  - Avoid hardcoding secrets.
  - Printing fetched secret to confirm dynamic retrieval.

### e) docs/usage_guide.md

- Detailed manual on how to:
  - Install dependencies.
  - Run install scripts.
  - Initialize Vault server and apply policies.
  - Use GitLeaks to detect secrets.
  - Rotate secrets securely.
  - Understand zero trust principles applied.

---

## 4. Step-by-Step Development Workflow

### Step 1: Setup Environment
- Clone the repo.
- Run `scripts/install_gitleaks.sh` to install GitLeaks.
- Run `scripts/install_vault.sh` to install Vault.

### Step 2: Create Test Git Repository
- Use `detect_leaks.sh` to create a repo with a secret committed.
- Run GitLeaks scan to detect the secret leak.

### Step 3: Setup Vault
- Run `vault_setup.sh` to:
  - Start Vault dev server.
  - Export necessary environment variables.
  - Enable KV secrets engine.
  - Create and apply least privilege policies.
  - Generate restricted tokens.

### Step 4: Secure Secret Storage & Access
- Use Vault CLI or API to store secrets securely.
- Update source code (`src/sample_code.py`) to read secrets from Vault via environment variables.

### Step 5: Secret Rotation
- Use `rotate_secrets.sh` to revoke leaked keys and generate new keys.
- Commit updated code without hardcoded secrets.

### Step 6: Ignore Known Leaks
- Add leak fingerprints to `vault_ignore_file.gitleaksignore`.
- Use this file in GitLeaks to avoid false positives on known commits.

---

## 5. Additional Recommendations for GitHub

- Add `.gitignore` to exclude local Vault tokens or sensitive environment files.
- Use GitHub Actions in `.github/workflows/` to automate GitLeaks scanning on every push.
- Document project with clear commit messages reflecting secret management best practices.
- Include security warnings about never hardcoding secrets.

---

## 6. Summary

By structuring your GitHub project with the above organization, scripts, and documentation, you convert the practical video demonstration into a reusable, maintainable, and industry-grade secret management and zero trust implementation project.

This approach helps:

- Detect leaked secrets early using GitLeaks.
- Securely manage secrets using HashiCorp Vault.
- Implement zero trust with least privilege policies.
- Automate scanning and secret rotation.
- Avoid hardcoding secrets in source code.

---
**Gitleaks-Installation-on-Ubuntu**
# Gitleaks Installation
wget https://github.com/gitleaks/gitleaks/releases/download/v8.18.2/gitleaks_8.18.2_linux_x64.tar.gz
tar -xvzf gitleaks_8.18.2_linux_x64.tar.gz
sudo mv gitleaks /usr/local/bin/

api_key = AKIAIMNO78987EXAMPLE
