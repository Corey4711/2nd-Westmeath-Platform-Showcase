# Feature workflows

## Public website

The public site provides section information, activities, badges, life-skills content, group history, safeguarding material, frequently asked questions and contact routes. It also surfaces public social content from Facebook, Instagram and YouTube and links visitors to the group’s other public channels.

Registration and payment pages use explicit indexing controls so operational journeys do not become search landing pages.

## Registration and consent

Parents submit a combined registration and consent form with client- and server-side validation. The submission records the declaration version and electronic signature, then opens a hosted payment session. A parent can resume an incomplete payment without entering the registration again.

Consent documents are generated from the official form template. Parent download is tied to confirmed payment; authorized leaders can retrieve individual documents or scoped archives, with downloads recorded for audit.

## Scout profiles and history

The leader portal groups a Scout’s year-by-year registrations with relevant camp payments, subscriptions, custom payments and attendance. Section and finance permissions determine which parts of that history a leader can view.

Historical records are joined only when the match is unambiguous. This reduces duplicate profiles without silently assigning records to the wrong person.

## Camps, subscriptions and payment requests

Camp management supports deposits, balances, annual or variable amounts, status summaries and payment history. Leaders can create payment items for activities that do not fit the standard flows.

Recurring subscriptions use hosted subscription Checkout and provide parent access to Stripe’s customer portal. The local application retains the subscription and invoice state needed for leader administration and reconciliation.

Custom payment requests cover subscriptions, camps and other purposes. The request is emailed with a hosted payment link, then linked back to the appropriate operational record after provider confirmation.

## Attendance

Leaders can create standard or additional meetings, prepare a draft roster and complete attendance. Meetings can also be marked as having no Scouting activity. Membership periods determine who is eligible for each meeting, while the saved roster preserves what was recorded at the time.

The Ventures workflow adds notified absence and uniform status, including full uniform, hoodie and missing-item detail. Summary statistics are derived from the saved meeting data.

## Email management

Transactional messages cover registration reminders and confirmations, camp confirmations, subscription confirmations and custom payment requests. Authorized leaders can inspect delivery history, retry supported messages, export appropriate records and send controlled test messages.

The worker checks current application state before delivery. This prevents a queued reminder from being sent after the underlying action has already been completed.

## Leader administration and audit

Role and section assignments control access to registration, finance, attendance, email and administrative functions. Authorization is enforced on the server for every protected operation rather than relying on hidden frontend controls.

Audit views bring together protected record access, changes, exports, document downloads and unsuccessful or denied operations. Metadata is filtered before storage so the audit trail does not become a second copy of sensitive content.
