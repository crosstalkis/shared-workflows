# shared-workflows

Reusable workflows + composite actions for the `crosstalkis` org. Mirrors the "single source-of-truth for delivery primitives" pattern we'd deploy at ČSAS.

## Contents

| Path | Purpose |
|---|---|
| `.github/workflows/conjur-fetch.yml` | Reusable workflow. Callers invoke as `uses: crosstalkis/shared-workflows/.github/workflows/conjur-fetch.yml@v1` |
| `.github/actions/conjur-jwt-fetch/action.yml` | Composite action that does the Conjur JWT exchange via curl. No third-party actions — auditability. |

## Versioning

Pinned via the `v1` tag. Bumping the version is a deliberate rollout decision.

## Phase-2 lab scope

- Conjur is reachable at the in-cluster Service DNS `https://conjur-oss.conjur.svc.cluster.local` (runners are in-cluster, no public exposure).
- Conjur trusts the runner's `repository`/`ref` claims from the GHA OIDC JWT.
- Secret retrieved: `lab/secrets/test-secret`.
- Phase 3 will switch to org-level `sub` customization so multiple repos in the same app fold to one Conjur identity.
