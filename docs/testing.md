# Testing strategy

The test suite separates fast application feedback from database and full-browser verification. Test environments use synthetic records and fake payment services rather than production data or live payment activity.

| Layer | Purpose | Tooling |
| --- | --- | --- |
| Frontend unit tests | Components, forms, services and client-side behaviour | Jasmine and Karma |
| API tests | Validation, authorization, transformations and provider-event handling | Vitest |
| Database tests | Access policies, functions, triggers and data invariants | pgTAP |
| Mocked browser tests | Fast coverage of important user journeys with controlled network responses | Playwright |
| Isolated end-to-end tests | Browser, API and database behaviour across realistic workflows | Playwright with an isolated Supabase environment and fake Stripe services |
| Static and build checks | Type safety, lint rules and production compilation | TypeScript, ESLint and the Angular production build |

## Workflow coverage

Automated scenarios cover the workflows where state crosses system boundaries, including:

- registration validation, consent state and resuming incomplete payment;
- role- and section-based leader access;
- payment event processing, duplicate delivery and reconciliation;
- Scout history and permission-limited finance data;
- attendance roster derivation, historical preservation and edit conflicts;
- email claiming, suppression, retry and delivery-state updates;
- consent document authorization and audit recording.

## Local and CI execution

Developers can run an aggregate local verification that includes frontend, API, database and browser tests. The database-backed suite starts isolated services, applies migrations and seed data, and uses a local payment double.

GitHub Actions runs on pull requests to `master` and `preview` and can also be started manually. The workflow installs locked dependencies, runs linting, API type checks and API tests, builds the application, executes the mocked and database-backed browser suites, and retains browser-test diagnostics when needed. Frontend unit tests and the standalone pgTAP suite remain part of the aggregate local verification.

Test-case totals are deliberately omitted because they change as the platform evolves. The important distinction is the boundary each layer verifies and the use of isolated, synthetic state for integration testing.
