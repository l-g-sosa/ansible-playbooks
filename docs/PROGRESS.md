
---

## `docs/PROGRESS.md`

```markdown
# PROGRESS.md
## Ansible Automation Platform – Learning Progress

This file tracks **what has been completed**, **what is in progress**, and **what comes next**.

---

## ✅ Completed Milestones

### Git & Repo
- Created GitHub repository: `ansible-playbooks`
- Established GitOps directory structure
- Fixed early mistake: empty playbook pushed → corrected and re-synced
- SSH key authentication to GitHub configured

### AAP Core Setup
- Containerized AAP running successfully
- Controller services verified via podman
- Organization created: HomeLab
- Source Control credential created and working
- Project created and syncing correctly from GitHub

### Inventory & Access
- Inventory moved to Git (YAML-based)
- Host vars and groups structured correctly
- Managed node reachable via SSH
- Become (sudo) working correctly in AAP jobs

### First Automations
- ✅ Ping playbook created
- ✅ Ping Job Template created
- ✅ Ping Job executed successfully against managed01

### Baseline Automation
- Created `baseline.yml`
- Fixed empty-file Git issue
- Playbook now visible in AAP after sync
- VS Code used successfully as editor + Git client

---

## 🟡 In Progress

- Running baseline playbook as a Job Template
- Verifying idempotence (second run = no changes)
- Improving VS Code Ansible experience (extensions, validation)

---

## ⏭️ Next Planned Tasks (Near-Term)

### Playbook Improvements
- Add:
  - Handlers
  - Templates (`template:` module)
  - Tags (`--tags`, `--skip-tags`)
  - Conditionals
- Convert baseline tasks into a **role**

### AAP Features
- Surveys (prompt for username / package list)
- Workflow Templates
- RBAC (teams, limited users)
- Credential best practices

### Quality & Professionalism
- Ansible-lint integration
- Naming conventions
- Role-based repo layout
- Documentation per playbook

---

## 🎯 Long-Term Goals

- Production-grade playbooks
- Confidence reading & modifying enterprise playbooks
- Real AAP usage at work (projects, workflows, approvals)
- RHCSA → RHCE alignment

---

Last updated: 2026-01-28
