# AI Repository Bootstrap

This repository is the starting point for a new private AI/agent project.

## Day-zero repository state

Before application code is added:

1. Create the target repository as **private** unless the project is intentionally open source.
2. Start from this hardened template.
3. Keep `main` protected. Require pull requests, an independent approving review, required security checks, resolved conversations, and block force-push/deletion.
4. Enable Dependency Graph, secret scanning, and push protection where the GitHub account/plan supports them.
5. Keep repository-level auto-merge optional. It must never bypass reviews or required checks.
6. Keep production secrets out of repository contents.

## Environments

Use three logical environments:

- `development`: local or disposable developer resources.
- `staging`: integration tests and pre-production deployments.
- `production`: protected production resources.

Production credentials must not be reused in development or staging.

## AI/provider boundary

Provider credentials belong in the provider or GitHub secret store, not in source code.

Expected secret names are documented in `.env.example`. The example file contains empty placeholders only.

Model routing should explicitly define:

- approved providers/models;
- request timeouts and retry policy;
- cost/usage ceilings;
- fallback behavior;
- privacy/data-retention constraints;
- tool/action permissions.

Model output is untrusted input until validated.

## CI/security baseline

The template is wired to the account-wide immutable governance release for:

- exact Python runtime baseline;
- Privacy Guard;
- source-aware CodeQL;
- OpenSSF Scorecard;
- Dependency Review capability checks.

A central repository-policy gate is added once its account-wide release is verified and merged.

## Cloud/deploy boundary

Prefer short-lived identity federation/OIDC over long-lived tokens where supported.

Separate:

- build identity;
- deploy identity;
- database identity;
- model-provider identity;
- monitoring identity.

A compromise of one provider must not automatically compromise the others.

## Release evidence

Every production release should record at minimum:

- source commit SHA;
- build workflow/run ID;
- artifact SHA-256;
- SBOM where supported;
- provenance/attestation where supported;
- deployment environment;
- rollback reference.

## Backup and recovery

Back up source and release evidence outside the primary GitHub repository.

Recovery drills should prove:

- repository restoration;
- secret rotation;
- provider revocation;
- database restore where applicable;
- rollback to the last verified release.

## Completion rule

A checkbox, config file, or historical run is not proof. A control is PASS only when it is verified for the exact repository, branch, commit, environment, or artifact being evaluated.
