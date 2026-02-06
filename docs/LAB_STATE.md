# LAB_STATE.md

## Immediate Next Session Goals
- Run the `baseline.yml` playbook successfully from AAP
- Compare AAP execution output with local CLI output
- Confirm idempotence in AAP (second run = no changes)

---

## Skills to Deepen
- Handlers and event-driven restarts
- Service configuration management with templates
- Clear separation between “ensure installed” and “ensure configured”

---

## Gaps to Close
- No handlers implemented yet
- Time sync service is managed but not configured
- No validation yet of AAP execution environment behavior

---

## Specific Tasks to Attempt
1. Add `handlers/main.yml` to the `common` role
2. Create `templates/chrony.conf.j2`
3. Update role to deploy `chrony.conf` using `template`
4. Add `notify: restart chronyd`
5. Implement handler:
   - name: restart chronyd
   - service: restarted

---

## Start Here Next Session
1. Upload `LEARNED.md` and `NEXT_STEPS.md`
2. Sync AAP Project
3. Launch Job Template with `playbooks/baseline.yml`
4. Observe and compare results vs local runs

---

## Target Skill Upgrades
- Roles: Practiced → Comfortable
- Templates (Jinja2): Practiced → Comfortable
- Handlers: Not Started → Practiced
- AAP Job Templates: Practiced → Comfortable
