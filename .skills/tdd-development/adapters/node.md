# TDD Adapter: Node

## Detection

- `package.json`
- Lockfiles such as `package-lock.json`, `pnpm-lock.yaml`, or `yarn.lock`

## Test Strategy

- Prefer existing Jest, Vitest, Mocha, Playwright, or framework-specific tests.
- Use the package manager already used by the repository.
- Keep unit and end-to-end tests separate.

## Commands

- npm: `npm test`
- pnpm: `pnpm test`
- yarn: `yarn test`

## Review Risks

- Snapshot churn.
- Unmocked network calls.
- Flaky browser tests.
