# LAB_STATE.md
## Ansible Automation Platform – Home Lab State

This document is the **source of truth** for the current AAP lab environment.
It reflects the actual, verified state as of the end of the last session.

---

## 1. Architecture Overview

### Control Plane
- **Platform**: Red Hat Ansible Automation Platform (AAP)
- **Deployment type**: Containerized AAP
- **Controller URL**: https://192.168.68.83
- **Controller host**: aap-controller (VM)
- **Execution model**: Controller-managed execution environments
- **Primary use**: Learning and production-style automation practice

### Managed Nodes
- **managed01**
  - OS: RHEL 9
  - IP: 192.168.68.81
  - SSH user: ansible
  - Authentication: SSH key-based
  - Privilege escalation: sudo via become
  - Connectivity: Verified from AAP

---

## 2. GitOps Repository (Source of Truth)

### GitHub
- **Repository**: https://github.com/l-g-sosa/ansible-playbooks
- **Default branch**: main
- **Workflow**:
  - VS Code used for editing
  - Local Git commits as non-root user
  - Push to GitHub
  - AAP Project sync pulls changes

### Repository Structure
```text
ansible-playbooks/
├── inventories/
│   └── lab/
│       ├── hosts.yml
│       ├── group_vars/
│       │   └── all.yml
│       └── host_vars/
│           └── managed01.yml
├── playbooks/
│   ├── ping.yml
│   └── baseline.yml
└── docs/
    ├── LAB_STATE.md
    └── PROGRESS.md
```

---

## 3. Inventory Model

- Inventory is YAML-based and stored in Git
- Group and host variables separated correctly
- Inventory is synced into AAP via Project
- Inventory successfully used by Job Templates

---

## 4. Credentials & Access

### AAP Credentials
- **Source Control Credential**
  - Type: Git
  - Authentication: SSH key
  - Status: Working, project sync successful

- **Machine Credential**
  - SSH private key for user `ansible`
  - Become enabled
  - Verified working in job runs

---

## 5. AAP Objects in Use

- **Organization**: HomeLab
- **Project**: ansible-playbooks (Git-backed, auto-sync)
- **Inventory**: Lab inventory (Git-based)
- **Job Templates**:
  - Ping test job
  - Baseline configuration job

---

## 6. Baseline Playbook Status

- `playbooks/baseline.yml` exists and is active
- Tasks included:
  - opsuser creation and wheel membership
  - Passwordless sudo via `/etc/sudoers.d`
  - Baseline package installation
  - sshd service enablement
  - MOTD banner management
- Tags implemented:
  - users
  - sudo
  - packages
  - services
  - banner
- **Idempotence verified**:
  - Second AAP run reports `changed=0`

---

## 7. Development Workflow Notes

- Git commits must be performed **without sudo**
- Git user.name and user.email configured for normal user
- Root usage restricted to system operations only
- Ownership issues resolved with `chown` where needed

---

## 8. Known Constraints / Gotchas

- Using `sudo git commit` causes author identity errors
- Root-owned repo files break Git workflows
- Idempotence must be validated in AAP, not only via CLI
- Tags must be kept clean (no trailing whitespace) to avoid lint noise
