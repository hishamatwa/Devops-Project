# Security Review - Voting App (kind / Kubernetes)

## Scope
Services: vote, result, worker, redis, db (PostgreSQL). Namespace: voting-app.

## Key findings (current state)
1) Secrets: DB password is stored in plain text in YAML env variables.
2) Storage: DB uses emptyDir (data is lost if the pod is recreated).
3) Images: some images use the `latest` tag (not reproducible).
4) Network: no NetworkPolicies (pods can talk freely by default).
5) RBAC: default ServiceAccount is used (no least-privilege roles).
6) Reliability: no readiness/liveness probes; replicas=1.

## Risks
- Credentials exposure if manifests are shared or committed.
- Data loss on restart/recreate for the database.
- Uncontrolled updates when using `latest`.
- Easier lateral movement if a pod is compromised.
- Harder to detect unhealthy pods without probes.

## Recommended next steps (production-grade)
- Use Kubernetes Secret for DB credentials.
- Use PVC for DB persistence + define a backup plan.
- Pin images to version tags or digests (no `latest`).
- Add resource requests/limits and health probes.
- Add NetworkPolicies and least-privilege RBAC.

