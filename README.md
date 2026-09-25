```txt
npm install
npm run dev
```

```txt
npm run deploy
```

[For generating/synchronizing types based on your Worker configuration run](https://developers.cloudflare.com/workers/wrangler/commands/#types):

```txt
npm run cf-typegen
```

Pass the `CloudflareBindings` as generics when instantiation `Hono`:

```ts
// src/index.ts
const app = new Hono<{ Bindings: CloudflareBindings }>()
```

## Project context and engineering approach

This is the API foundation for Moveto blog content. It runs on Cloudflare Workers so content endpoints can be deployed close to readers while keeping runtime configuration typed through generated Worker bindings.

Hono provides the routing layer, Better Auth supplies an authentication option, and Drizzle ORM provides a data-model boundary. `cf-typegen` prevents Worker bindings from becoming untyped configuration, while the development and deployment commands keep the local-to-Cloudflare workflow explicit.

## Technology

- Cloudflare Workers and Wrangler for the serverless runtime and deployment
- Hono for typed HTTP routing
- Better Auth and Drizzle ORM for identity and data boundaries
- TypeScript with generated Cloudflare binding definitions

## Status

Early API service repository retained for further blog-platform development.
