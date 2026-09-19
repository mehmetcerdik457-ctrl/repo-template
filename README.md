# Hardened Project Template

This repository is the default starting point for new projects.

Baseline expectations:

- pull-request based changes for protected branches;
- least-privilege GitHub Actions permissions;
- pinned third-party Actions;
- Dependabot for GitHub Actions and project dependencies;
- no secrets, tokens, signing keys, keystores, recovery codes, or private credentials in source control;
- CODEOWNERS and review ownership;
- explicit security reporting guidance;
- reproducible verification evidence for release, security, CI/CD, and infrastructure changes.

Project-specific repositories should add the language/build-specific security scanners, tests, release workflow, SBOM generation, provenance attestations, and environment protections they actually need.
