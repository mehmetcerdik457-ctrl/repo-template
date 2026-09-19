# Connector and Provider Boundaries

Treat every external integration as an independent trust boundary.

## AI/model providers

Examples: OpenAI and Hugging Face.

- keep credentials provider-specific;
- grant minimum scopes;
- separate development and production credentials;
- enforce model/cost/tool allow-lists in application policy.

## Database/state providers

Examples: Supabase, Neon, or another managed Postgres provider.

- use environment-specific databases;
- restrict service-role/admin credentials to server-side workloads;
- never expose privileged keys to mobile/web clients.

## Deployment providers

Examples: Vercel and Railway.

- use separate staging/production projects or environments;
- prefer federated/short-lived deployment identity;
- do not give build jobs broad account administration privileges.

## Operations

Examples: Slack and Datadog.

- notification integrations should not receive unrelated source/secrets;
- monitoring write access is separate from read-only investigation access;
- production alert destinations should be explicit.

## Backup

Use an independent backup destination such as Drive or Dropbox for recovery evidence when approved.

Backups must not become a second uncontrolled secret store.

## Rule

Connecting a provider does not make GitHub the owner of that provider account. GitHub orchestrates narrowly scoped credentials and workflows; provider-side access remains governed by that provider.
