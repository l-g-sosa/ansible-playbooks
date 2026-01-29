# LAB_STATE.md
## Ansible Automation Platform – Home Lab State

This document is the **source of truth** for my AAP lab environment.
Any trainer, assistant, or collaborator should read this first.

---

## 1. Architecture Overview

### Control Plane
- **Platform**: Red Hat Ansible Automation Platform (AAP)
- **Deployment type**: Containerized AAP
- **Controller URL**: https://192.168.68.83
- **Controller host**: aap-controller (VM)
- **Execution model**: Controller-managed execution environments
- **Primary use**: Learning + production-style automation practice

### Managed Nodes
- **managed01**
  - OS: RHEL 9
  - IP: 192.168.68.81
  - SSH user: ansible
  - Access: SSH key-based authentication
  - Privilege escalation: sudo via become

---

## 2. GitOps Layout (Source of Truth)

### GitHub Repository
- **Repo URL**: https://github.com/l-g-sosa/ansible-playbooks
- **Branch**: main
- **Repo purpose**:
  - Inventories
  - Host/group variables
  - Playbooks
  - Documentation (this file)

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
