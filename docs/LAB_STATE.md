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

