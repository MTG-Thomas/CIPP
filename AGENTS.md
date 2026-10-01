# CIPP guidance

This fork contains the CIPP Microsoft partner administration frontend. Read [README](README.md), [contribution rules](CONTRIBUTING.md), and the existing `.github/agents/` task instructions when relevant. Preserve upstream licensing and CLA documents. Keep local fork changes distinguishable from upstream updates.

Inspect `src/` for the affected page, shared component and API caller before editing. This is the frontend repository; do not invent a backend implementation here or assume an MTG deployment from checked-in Azure templates. Changes involving tenant selection, delegated administration, permissions or bulk actions must preserve their existing authorization and failure paths. Use synthetic tenant data in fixtures and never commit tokens or customer records.

## Development and verification

`package.json` declares Node `^22.13.0`. The upstream Node workflow installs with `npm install --legacy-peer-deps` and builds with `npm run build`. The build script deletes root `package.json` and `yarn.lock` after Next.js completes: run it only in a disposable checkout and preserve the reviewed source. `npm run dev` starts Next.js on loopback; inspect the configured emulator setup before invoking it against an API.

The Node build job is owner-guarded to `KelvinTegelaar`; its presence does not prove build coverage for this fork. `npm run lint` is declared, but verify it works with the installed Next.js version before treating it as a passing gate. Report the exact checks actually executed and browser/API boundaries not exercised.

The PR workflow closes fork PRs targeting `main`/`master` or originating from a fork's `main`/`master`. Verify the intended development branch before publishing a PR; do not bypass that workflow. Deployment workflows and Azure template changes need their own scoped review and authorized environment lane.
