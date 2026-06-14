# Genql Rate Limits

Genql is a client-side code generation tool and TypeScript library. It does not expose a hosted API service with its own rate limits. The `@genql/cli` package runs locally or in CI/CD pipelines to generate a typed client from your GraphQL schema — this generation step is a build-time operation with no external rate limiting imposed by Genql.

## Build-Time Generation

The `genql` CLI fetches your GraphQL schema once (via introspection or a local schema file) and generates client code. This is typically run:

- During local development
- As part of a CI/CD pipeline on schema changes

No Genql-imposed limits apply to this step.

## Runtime (Generated Client)

The generated client makes HTTP requests to **your** GraphQL endpoint. Rate limits at runtime are governed entirely by the GraphQL service being called, not by Genql.

### Built-in Retry Support

The generated client supports configurable retry logic to help handle transient failures and downstream rate limit responses (HTTP 429). Implement exponential backoff in the retry configuration when connecting to rate-limited GraphQL services.

### Batching

Genql supports batched queries, which can help reduce the total number of HTTP requests sent to a downstream GraphQL endpoint — an effective technique for staying within rate limits imposed by external services.

## Notes

For rate limits on any specific GraphQL API you connect to via Genql, consult that provider's documentation. Genql itself imposes no request quotas or throttling.
