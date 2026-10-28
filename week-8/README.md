# Week 8: Security Hardening and Shifting Left

## What changed
- Tightened file permissions on the VM (state files and deploy log are 600).
- Web pod runs as non-root (uid 10001), drops all capabilities, and has CPU/memory limits.
- Database pod has CPU/memory limits.
- NetworkPolicy `db-from-web-only` allows only web pods to reach the database on port 5432.
- Deploy gate now runs on pull requests and includes a Checkov security scan.
- GitHub ruleset requires a pull request and the three gate checks before merge to main.
- Deploy script saves a plan and stops if the plan would delete or replace any resource.

## Where things live
- OpenTofu: `week-5/`
- Gate workflow: `.github/workflows/deploy-gate.yml`
- Deploy script: `week-7/deploy.sh`
- Ruleset definition: `week-8/ruleset.json`

## Verify
- `kubectl exec deploy/web -- id` → uid=10001
- `kubectl get networkpolicy` → db-from-web-only
- Probe without `app=web` label cannot reach db; probe with the label can.

## Known limits
- The scan only checks the rules listed in the workflow.
- The ruleset can be deleted by a repo admin.
- The deploy stop only catches deletions/replacements visible in the plan.
