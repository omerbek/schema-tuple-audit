# Schema Tuple Audit

This is an **independently published, modified derivative** of [Zod](https://github.com/colinhacks/zod), not an official Zod release or a new schema library. The source retains Zod's original Git history, authorship, package names, and MIT license. See the [upstream README](packages/zod/README.md) for Zod's API and documentation; upstream package links and release instructions do not publish this repository's changes.

This branch corrects [Zod issue #6651](https://github.com/colinhacks/zod/issues/6651): the JSON Schema emitter previously wrote invalid empty `prefixItems`, tuple-form `items`, or `anyOf` arrays for an empty tuple. A closed empty tuple now has `maxItems: 0` with valid dialect-specific item keywords. An empty tuple with `.rest(...)` applies its rest schema to every item in draft 2020-12, draft-7, and OpenAPI 3.0 output. The issue's reporter is credited in the linked report.

For local source verification, install the upstream-pinned Nub 0.8.3 and run:

```sh
nub install --frozen-lockfile
nub exec --node vitest run packages/zod/src/v4/classic/tests/to-json-schema.test.ts
nub run build
```

The GitHub workflow in this derivative only tests and builds source. Upstream publishing, scheduling, and agent automations are intentionally removed so a separately owned repository cannot release Zod packages or act on issues using inherited workflows.
