---
'@modelcontextprotocol/server': patch
---

fix(server): re-export AjvJsonSchemaValidator and CfWorkerJsonSchemaValidator from root index

The type declarations (`dist/index.d.mts`) already listed `AjvJsonSchemaValidator`,
`CfWorkerJsonSchemaValidator`, and `CfWorkerSchemaDraft` as root exports, but the
runtime `dist/index.mjs` omitted them. Consumers importing from
`@modelcontextprotocol/server` hit a `SyntaxError` at runtime.

This adds the missing re-exports to `packages/server/src/index.ts`, matching the
existing subpath exports at `./validators/ajv` and `./validators/cf-worker`.
