# Genql FinOps

Genql is a free, open-source MIT-licensed tool. There are no licensing fees, subscription costs, or usage-based charges for Genql itself. The FinOps considerations for teams using Genql relate to the infrastructure and GraphQL services that the generated client connects to.

## Direct Costs: None

| Item | Cost |
|------|------|
| @genql/cli (npm) | Free |
| GitHub repository | Free |
| Code generation runs | Free |
| Generated client library | Free |

## Indirect Cost Drivers

Although Genql itself is free, teams should track costs in adjacent areas:

### 1. Downstream GraphQL API Costs
The generated client makes requests to external GraphQL endpoints. API usage costs, rate-limit overages, and data egress fees are charged by the GraphQL service provider, not Genql.

**Optimization tips:**
- Use Genql's batching feature to reduce total HTTP requests
- Fetch only needed fields rather than using `__scalar: true` in high-volume scenarios
- Cache introspection results to avoid repeated schema fetches in CI/CD

### 2. CI/CD Compute
Running `genql` in a CI/CD pipeline consumes build minutes. Schema generation is fast (seconds), so costs are minimal but should be considered for high-frequency pipelines.

### 3. Developer Tooling Time
Code generation eliminates manual query writing and reduces type errors caught late. This yields positive ROI through reduced developer debugging time.

## Cost Allocation Tags

When tracking API costs for services called by a Genql-generated client, apply these dimensions to your cost allocation:

| Dimension | Example Values |
|-----------|---------------|
| service | graphql-api-name |
| environment | production, staging, development |
| team | backend, frontend, data |
| feature | search, checkout, reporting |

## Summary

Genql has zero direct licensing cost. FinOps practices for Genql users should focus on the downstream GraphQL APIs the generated client calls, CI/CD build cost, and developer productivity gains from type-safe query generation.
