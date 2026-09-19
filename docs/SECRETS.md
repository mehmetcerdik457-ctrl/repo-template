# Secret Handling Contract

## Never commit

Do not commit:

- API keys or access tokens;
- private keys or certificates with private material;
- Android keystores/signing credentials;
- database passwords or service-role keys;
- recovery codes;
- OAuth client secrets;
- webhook secrets;
- production environment files;
- private datasets or credentials embedded in test fixtures.

## Storage

Use the narrowest authorized secret store available:

- GitHub Environment secrets for protected deployments;
- deployment-provider secret stores for provider-local runtime secrets;
- local untracked `.env` only for development;
- short-lived OIDC/federated credentials instead of long-lived cloud credentials where supported.

## Separation

Use different credentials for development, staging, and production.

Do not reuse a production API key in CI tests.

## Rotation

When exposure is suspected:

1. revoke or rotate the credential;
2. invalidate dependent sessions/tokens;
3. inspect Actions logs, artifacts, commits, issues, and deployments;
4. remove the exposed value from active configuration;
5. record incident evidence without republishing the secret.

Deleting a secret from the latest commit does not revoke it.

## CI behavior

CI may verify that a secret name is wired, but must not print the secret value.

Paid/external API probes should be explicit and bounded rather than silently triggered by every pull request.
