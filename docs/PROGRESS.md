# PROGRESS.md
## Ansible Automation Platform – Learning Progress

Tracks what is complete, what is in progress, and what comes next.

---

## ✅ Completed This Session

### Git & Workflow
- Git author identity configured correctly (non-root)
- Root Git usage identified as an anti-pattern and corrected
- Successful commit and push workflow re-established

### Baseline Playbook
- `baseline.yml` updated with:
  - Explicit user shell
  - Consistent task tagging
- Baseline Job Template executed twice in AAP
- **Idempotence confirmed**:
  - Second run: `ok=6 changed=0 failed=0`

### AAP Validation
- Baseline playbook runs cleanly via AAP
- Become works correctly
- No warnings or drift detected

---

## 🟡 In Progress

- Refactoring baseline playbook into a reusable **role**
- Deciding role structure and variable placement
- Preparing for template and handler usage

---

## ⏭️ Next Session Planned Work

### Roles & Structure
- Create `roles/baseline/`
- Move tasks into role task files
- Decide placement for MOTD content (template vs static)
- Introduce handlers where appropriate

### AAP Enhancements
- Update Job Template to use role-based playbook
- Introduce tags usage in AAP job runs
- Begin workflow-template discussion

### Quality Improvements
- Introduce ansible-lint considerations
- Naming conventions aligned with enterprise repos
- Documentation per role

---

## 🎯 Long-Term Direction

- Production-grade role-based repository
- Comfortable navigation of enterprise Ansible codebases
- Confident use of AAP features (workflows, RBAC, surveys)
- Alignment with RHCE-level expectations
