# Nx Monorepo Starter

Badges: Next.js · TypeScript · Tailwind CSS · Nx · Cloudflare Workers · pnpm · github actions 

## Overview
This repository is a stable Nx-based monorepo template. It is structured to host multiple apps and shared packages with consistent tooling, fast builds, and repeatable deployment.

## Repository Layout
```
.
├── apps/
│   ├── web/         # Next.js web app
│   └── cf-server/   # Cloudflare Worker backend
├── packages/
│   └── api-endpoints/  # Shared API surface
├── tools/           # Custom Nx generators/executors (if added)
├── nx.json          # Nx workspace config
├── tsconfig.base.json
└── package.json
```

## Prerequisites
- Node.js LTS (check `.nvmrc` or set your preferred LTS)
- pnpm (recommended): `npm install -g pnpm`

## Quick Start
```bash
git clone <your-repo-url>
cd main-codebase
pnpm install
pnpm nx graph   # optional: visualize dependencies
pnpm nx serve web
```
Visit http://localhost:3000 (auto-selects the next free port if 3000 is taken).

## Environment Setup
- Next.js app: create `apps/web/.env.local` for web secrets.
- Cloudflare Worker: use `wrangler.jsonc` plus `.dev.vars` for local secrets.
- Keep secrets out of version control.

## Common Commands
- Install deps: `pnpm install`
- Serve app: `pnpm nx serve web`
- Build app: `pnpm nx build web`
- Test: `pnpm nx test <app>`
- Lint: `pnpm nx lint <app>`
- Format (workspace): `pnpm nx format:write`

## Development Notes
- Prefer running tasks through Nx to leverage caching and affected commands.
- To run a target across projects: `pnpm nx run-many --target=build --projects=web,cf-server`
- To see what changed: `pnpm nx affected:graph` or `pnpm nx affected --target=build`

## Deployment
- Cloudflare Worker (cf-server): `cd apps/cf-server && pnpm wrangler deploy`
- Web (Next.js via OpenNext/Cloudflare): run `pnpm nx build web` then your chosen deploy step (e.g., `pnpm wrangler pages deploy out`). Adapt to your CI/CD pipeline.

## Contributing
- Branch naming suggestion: `feat/<name>`, `fix/<issue>`, `chore/<task>`, `docs/<topic>`.
- Write clear PR descriptions and keep changes small and reviewable.
- Ensure lint, tests, and builds pass before opening a PR.

## License

<div align="center">
Configured with ❤️ by the <a href="https://github.com/Adnan-the-coder">Adnan</a>
</div>
        