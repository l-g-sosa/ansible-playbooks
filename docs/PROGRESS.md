# PROGRESS.md

## Session Overview
This session focused on understanding and implementing Ansible **roles** in a realistic
Ansible Automation Platform (AAP) lab. The learner transitioned from monolithic playbooks
to role-based automation, validated execution locally and via SSH, and aligned local
development workflows with AAP GitOps practices.

---

## Roles & Playbook Architecture

### What was learned
- Conceptual difference between playbooks (orchestration) and roles (implementation)
- Why roles are essential for maintainability, reuse, and enterprise scale
- Standard Ansible role directory structure and conventions
- How roles are discovered using `roles_path`
- Why roles should expose tunables via `defaults/` and not hardcode values

### What was practiced
- Creating a `common` role from scratch
- Refactoring an existing baseline playbook into a role-based model
- Writing role tasks, defaults, and templates
- Running role-based playbooks locally with `ansible-playbook`

### Lessons learned
- Role task files must contain **only tasks**, not play headers
- YAML/Jinja quoting errors are common early pitfalls
- Small typos (`state` vs `stated`) can fully break automation
- Good role boundaries prevent future “kitchen sink” roles

### Mental models gained
- “Playbooks orchestrate, roles implement”
- “Defaults expose knobs; inventory defines policy”
- “If a playbook is mostly tasks, it wants to be roles”

### Skill Level Summary
| Concept | Level |
|------|------|
| YAML syntax & structure | Practiced |
| Playbooks & plays | Comfortable |
| Tasks & modules | Comfortable |
| Roles | Practiced |
| Idempotence | Practiced |

---

## Templates (Jinja2)

### What was learned
- Templates are just files with variable substitution
- Templates belong inside roles for encapsulation
- Using `template` vs `copy` appropriately

### What was practiced
- Creating a simple `motd.j2` template
- Deploying `/etc/motd` using a role template
- Validating idempotence with `--diff`

### Lessons learned
- Templates do not need to be complex to be valuable
- Variables should be defined outside templates (defaults/inventory)

### Skill Level Summary
| Concept | Level |
|------|------|
| Templates (Jinja2) | Practiced |

---

## Inventory, SSH, and Execution Context

### What was learned
- Managed nodes do **not** need Ansible installed
- Difference between AAP execution identity and local CLI identity
- Why “Too many authentication failures” happens
- How to safely support both local and AAP execution paths

### What was practiced
- Creating a dedicated local SSH key for lab use
- Installing public keys manually on a headless RHEL VM
- Running Ansible locally using `--private-key`
- Verifying connectivity with ad-hoc `ping`

### Lessons learned
- Never store private key paths in Git
- AAP credentials ≠ developer laptop credentials
- SSH agent and `IdentitiesOnly` are critical tools

### Mental models gained
- “Control node runs Ansible, managed nodes are passive”
- “AAP credentials are production identities; laptop keys are dev identities”

### Skill Level Summary
| Concept | Level |
|------|------|
| Inventory & host grouping | Comfortable |
| SSH authentication | Comfortable |
| Privilege escalation (become) | Practiced |
| Error handling & debugging | Comfortable |

---

## AAP Platform Integration

### What was learned
- AAP Projects are Git checkouts, not browsable file trees
- The Job Template playbook dropdown is the authoritative view
- Why Git is the source of truth, not the UI

### What was practiced
- Aligning local repo layout with AAP expectations
- Understanding how AAP resolves roles and playbooks
- Preparing a role-based repo for AAP execution

### Skill Level Summary
| Concept | Level |
|------|------|
| GitOps workflow | Comfortable |
| AAP Projects | Practiced |
| AAP Job Templates | Practiced |
