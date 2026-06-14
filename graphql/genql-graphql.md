# Genql GraphQL API

Genql is a TypeScript code generator and type-safe GraphQL client library. It does **not** expose a hosted GraphQL server or API endpoint of its own. Instead, it reads any GraphQL schema (from a local file or a remote HTTP endpoint) and generates a fully-typed TypeScript client that can communicate with that target schema's server.

The library is published as `@genql/cli` (CLI) and its runtime is embedded inside each generated client. The public API surface consists of the CLI configuration interface, the `createClient` factory, and the set of types the generated client relies on at runtime.

**Endpoint:** N/A - library/tooling, no hosted endpoint

**Documentation:** https://genql.dev/docs

**Authentication:** Not applicable at the Genql library level. The generated client passes whatever `headers` (including `Authorization`) the caller supplies through to the target GraphQL server.

**References:**
- Documentation: https://genql.dev/docs
- GitHub: https://github.com/remorses/genql
- NPM (CLI): https://www.npmjs.com/package/@genql/cli
- Changelog: https://changelog.genql.dev
