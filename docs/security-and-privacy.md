# Security and privacy

The application processes youth membership, parent contact, consent and payment-related records. Its design keeps those records out of this public repository and limits access in the running system.

## Data boundary

- Browser clients use the application API and do not receive direct database credentials.
- Application tables are protected from public client roles; privileged database operations remain on the server.
- Protected responses use cache controls appropriate to private data.
- Sensitive application routes are excluded from search indexing.
- Consent documents are generated on demand and returned only after the relevant authorization or payment check.

## Authorization

Leader access is controlled by server-validated roles, capabilities and section assignments. The frontend reflects those permissions for usability, but it is not the authorization boundary. Finance data, member histories, document downloads, email administration and audit views each apply their own capability and section checks.

Authentication internals and session configuration are intentionally not documented here.

## Payments

Card and supported wallet details are collected on Stripe-hosted pages rather than by the application. Incoming payment events require provider signature verification. Local updates are idempotent so a repeated event does not create a second payment outcome.

The application supports multiple group and section payment contexts. Reconciliation compares local state with provider state and marks uncertain associations for review.

No production account identifiers, webhook addresses or live payment records are included in this repository.

## Auditing and restricted data

The API writes audit records for sensitive views, changes, downloads, exports and denied or failed actions. Download records cover consent documents as well as bulk retrieval. Audit metadata is reduced to an allow-listed shape before it is stored, limiting accidental duplication of personal data.

Audit access is itself permission-controlled and section-aware.

## Secrets and environments

Provider credentials and environment-specific secrets are held outside source control. Development and end-to-end tests use isolated resources and fake payment services. Environment-file layouts, internal endpoint addresses, provider identifiers and operational runbooks are intentionally not documented publicly.

## Information intentionally excluded

This public repository does not contain:

- production source code or operational configuration;
- real Scout, parent or leader data, live payment records or email-delivery records;
- raw database schemas that contain sensitive fields;
- authentication, session, identity-matching and abuse-control mechanics;
- secrets, account identifiers, callback addresses and exact schedules;
- operational incident and recovery procedures.

## Documentation scope

This documentation describes behaviour verified from the application source, migrations, tests and deployment configuration. Current external provider-dashboard configuration, organisation access policies and backup retention are outside the scope of this public technical overview.
