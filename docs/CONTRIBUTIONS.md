# My contributions: Nurin Irdina ([@nurinirdnz](https://github.com/nurinirdnz))

What I built on **SimeTown**, the township super-app our team made for the Sime Darby Property
University Hackathon 2026, taken from the project's git history (7 – 23 October 2026).
Every commit below can be checked with `git show <hash>`.

## In numbers

| | Me | Whole team | Share |
| --- | --- | --- | --- |
| Commits (excluding merges) | **34** | 67 | 51% |
| Lines added, excluding generated files¹ | **117,862** | 151,555 | 78% |
| Lines removed, excluding generated files¹ | **28,046** | 37,053 | 76% |
| Database migrations added or changed | **40** | 52 | 77% |
| Merges integrating teammates' branches and pull requests | **11** | | |

¹ `package-lock.json`, the generated `docs/API.md` and `docs/openapi.json`, images and the
scanner's WebAssembly file are left out. Counted with `git log --author --numstat`. Lines of
code are a rough measure; the sections below show what the work actually was.

## My role

- **Started the codebase.** The first commit set up the architecture the whole team builds on:
  - the Next.js app with one isolated backend (`src/server`);
  - the typed route table and router;
  - the double-entry points ledger, with its "no pool, no points" guards inside PostgreSQL;
  - sessions, roles and the test set-up.
- **Built the larger features end to end**: database migration, service rules, API, screens for
  every role involved, Malay translations, demo data, tests and docs, in the same commit.
- **Integrated the team's work.** I merged teammates' branches and pull requests into `main` and
  resolved conflicts between them. For example, smart lockers with home services and the Kitar
  tabs (`e2a55e3`), and the UI-polish pull request (`2c9b1fd`).
- **Owned security, DevOps and quality**: dependency CVEs, Node.js version pinning, Redis, CI/CD
  to GHCR, Docker fixes for hosted copies, session timeouts and the hosted-environment safeguards.

## Highlights

### Platform and architecture
- **Founding prototype** (`e8b2abb`, 172 files):
  - SimeTown ID and the points ledger, shops (give and accept points, statements), Points & XP;
  - Kitar, Gerak, Lapor, Jiran, Kongsi and Banjir;
  - the SDP console (campaigns, dashboard, float check, settlement).
  - Also: a shared Supabase PostgreSQL database, per-visitor rate limits, two-admin approval for admin accounts and password links, address capture from the property record, Terms and Privacy pages, a readable audit trail and 90 automated tests.
- **Upstash Redis** (`3ecdc41`):
  - Rate limits and a session cache, with automatic fallback to PostgreSQL and a 30 s pause after a failure.
  - A generation key clears every cached sign-in after commit on sign-out, password change and similar events.
  - Tests for the fallback and the invalidation.
- **Sign-in timeouts** (`f983e22`):
  - 15 min idle for staff, 30 min for others, none for guards on shift, and 12 h maximum.
  - Only real actions count, and this is enforced on the server.
  - A WCAG 2.2.1 warning with *Stay signed in*.
- **Hosted-environment safety** (`62b7538`): development mode is refused on a public address, so the development fallback keys can never run on the internet.

### Major features
- **Smart parcel lockers, courier platform and incidents** (`e2a55e3`, 163 files, 37,722 lines added):
  - Lockers: one-time PIN or QR pickup, keypad lockouts, door openings approved by a second admin, and a hardware adapter with a built-in simulator.
  - Couriers: courier companies approved per township, OpenID Connect sign-in with PKCE, and shipments checked against the label barcode, with one delivery per shipment enforced three ways.
  - Incidents: one engine with deadlines, escalations and a hash-chained history.
- **Private locker doors, guardhouse register and parcel emails** (`606400a`):
  - One door per home, and one guardhouse rule set.
  - A searchable register with each parcel's history.
  - Branded emails through a transactional outbox (nodemailer).
- **Guardhouse role** (`602d30a`):
  - A new `GUARDHOUSE` role, split from the gate guard.
  - Camera barcode and QR scanning on every device, with a self-hosted WebAssembly reader as fallback, which needed a CSP change.
- **Tamu visitor details** (`951db13`, `dfa8bc9`):
  - Citizenship, ID, transport, plate, licence expiry and reason. An expired licence blocks a vehicle.
  - ID numbers encrypted with AES-256-GCM: the full number goes to the guard only, and it is deleted after 90 days.
  - Passes sent by email.
- **Third edition** (`8e34286`, 205 files):
  - Tamu, guard tools, Akses+, smart recycling machines with signed records.
  - Gerak GPS tracking, the Banjir multi-signal flood agent, Shop Offers and sponsor tiers.
  - English / Bahasa Malaysia across every role.
- **AI Assistant** (`ac4d829`):
  - A server-side agent with tool calling, and actions only after the resident confirms.
  - OpenAI next to Anthropic.
  - Real City of Elmina loops (from OpenStreetMap) and real addresses.
  - A translation audit that runs in the tests.
- **Akses+ accessibility management** (`11ab780`):
  - Resident reports become routed incidents, with photo evidence and independent confirmation for every fix.
  - Configurable assignment rules and a retrying outbox for providers.
  - Also rebuilt the Shops console.
- **Lapor** (`2da5026`, `778dfb7`):
  - "Same problem, one issue" duplicate matching (AI with a rule-based fallback), and a 5-resident threshold before neighbours see a problem.
  - Junk and rude-word checks, Kitar and Gerak report tabs, and required photos.
  - Recycling collections that settle themselves from the gate record.
- **Gerak, Banjir and uploads** (`4586443`):
  - Gerak loops and challenges.
  - An ML-ready flood camera reader (your own model, then a hosted AI, then test pictures), and a development clock for the agents.
  - Image uploads rebuilt with `sharp` (content disarm and reconstruction).
- **Notifications center** (`920caa4`):
  - Filters, pagination, read and dismiss, and deep links.
  - Also archived three features (Taman, Greener materials, Jimat and Solar), each with a restore patch.

### UI, accessibility and languages
- **Public website** (`e048994`):
  - New landing page with an interactive *How it works*.
  - New pages: What we offer, Shops, Challenges, Sponsors & Partners.
  - Redesigned flood status and guest pages, and a demo-mode switch.
- **Premium console and role UI pass** (`d1f2e10`, 96 files): shared pills, KPI tiles, a data table, micro-interactions and 600 ms skeletons. Also repaired 52 corrupted Malay strings.
- **Accessible view and Simple Mode made independent** (`2b2897d`):
  - Rebuilt on a context provider, with styles that reach dialogs and overlays.
  - Checked at 25 addresses × 4 combinations × 3 widths with no axe WCAG 2.2 AA findings.
- **Complete Bahasa Malaysia** (`895cb79`):
  - Fixed the translator so it no longer produced half-Malay sentences.
  - Hardened it against slow input.
  - Checked against 13,399 samples.
- **"See how it works" walkthroughs** (`c49c1e6`, `3144e62`, `778dfb7`): for Parcels, Banjir, Lapor, Kitar and Gerak, across residents, guards, couriers and staff.

### Security, DevOps and maintenance
- **CD pipeline** (`eb575d2`): app and tools images published to GHCR after CI passes, with an optional deploy job that migrates, deploys and waits for `/api/v1/ready`.
- **Critical CVE response** (`e25e8aa`): upgraded Next.js 16.3.8 → 16.4.1 for two remote-code-execution flaws (CVSS 9.5).
- **Dependency hygiene** (`c53b12e`, `432dee6`): required patched Node.js versions (22.23.4+ / 24.22.1+), and applied only safe `npm audit` fixes.
- **Docker fixes for hosted copies** (`145846a`, `7c9a617`).
- **Migration and seed fixes** (`e220020`, `4c811ce`, `099c7cb`, `76c81c1`).

### Documentation
Wrote or substantially updated:
- the README;
- ARCHITECTURE, BUSINESS_RULES, SECURITY and DEPLOYMENT;
- NOTIFICATIONS, EMAIL_DESIGN, LANGUAGES, RISK_REGISTER and CONSOLE_UI_HANDOVER;
- DEMO_TESTING, and the archive restore guides.

## Every commit

| Date | Commit | What it did | Files | +/− lines |
| --- | --- | --- | --- | --- |
| 07 Oct | `e8b2abb` | SimeTown prototype: 11 of 12 plan features, shared database, security fixes | 172 | +31,742 |
| 12 Oct | `8e34286` | Third-edition features and bilingual support | 205 | +20,934 / −2,022 |
| 14 Oct | `ac4d829` | Real City of Elmina data, AI agent Assistant with history, full Malay coverage | 61 | +5,960 / −435 |
| 16 Oct | `e048994` | New public website, Sponsors & Partners, redesigned flood and guest pages, demo mode | 77 | +3,673 / −472 |
| 18 Oct | `e2a55e3` | Smart lockers, courier platform, incidents and Township of Tomorrow | 163 | +37,722 / −1,905 |
| 19 Oct | `920caa4` | Notifications center; remove Taman; archive Greener materials, Jimat and Solar | 94 | +6,605 / −7,270 |
| 19 Oct | `2c7e312` | Remove leftover Taman wording and unused translations | 5 | +6,373 / −6,486 |
| 19 Oct | `11ab780` | Automation-first Akses+ accessibility management; rebuild Shops console | 33 | +12,627 / −4,905 |
| 19 Oct | `3ecdc41` | Upstash Redis for rate limits and session cache; Insights fixes | 24 | +920 / −99 |
| 20 Oct | `e220020` | Renumber Kitar migration to avoid a duplicate | 2 | +9 |
| 21 Oct | `4c811ce` | Let HQ admins open Access places | 8 | +48 / −28 |
| 21 Oct | `d1f2e10` | Premium console and role UI pass | 96 | +14,462 / −12,937 |
| 22 Oct | `2da5026` | Lapor issues, Kitar/Gerak reports, demo data and UI polish | 99 | +5,340 / −979 |
| 22 Oct | `4586443` | Gerak loops & challenges, Banjir ML-ready reader, Akses+ routing, Lapor home service reports | 77 | +4,278 / −815 |
| 22 Oct | `eb575d2` | CD pipeline publishing Docker images to GHCR | 4 | +572 / −370 |
| 22 Oct | `895cb79` | Complete Bahasa Malaysia coverage; stop half-translated text | 14 | +444 / −112 |
| 22 Oct | `e25e8aa` | Update Next.js to 16.4.1 (critical CVEs); group the resident menu | 5 | +93 / −69 |
| 22 Oct | `c53b12e` | Require patched Node.js versions | 2 | +2 / −2 |
| 22 Oct | `432dee6` | Safe npm audit fixes for dev tools | 1 | +102 / −84 |
| 22 Oct | `2b2897d` | Accessible view and Simple Mode independent and consistent | 25 | +513 / −183 |
| 23 Oct | `606400a` | Private locker doors, guardhouse register, parcel emails | 72 | +7,026 / −2,646 |
| 23 Oct | `099c7cb` | Seed: one door per home on older databases | 1 | +9 / −5 |
| 23 Oct | `76c81c1` | Seed: add Locker C to older demo databases | 1 | +53 / −23 |
| 23 Oct | `c49c1e6` | Door commands in plain words, Parcels walkthroughs, guardhouse parcel bar | 27 | +1,115 / −52 |
| 23 Oct | `3144e62` | Banjir walkthroughs, colour-coded flood page, simulation banner | 10 | +623 / −94 |
| 23 Oct | `778dfb7` | Lapor photos, walkthroughs, self-settling Kitar collections, collection history | 98 | +2,557 / −249 |
| 23 Oct | `602d30a` | Separate Guardhouse staff role, restyled counter, camera scanning on every device | 45 | +426 / −139 |
| 23 Oct | `951db13` | Tamu visitor details at the gate: citizenship, ID, transport, licence, reason | 43 | +2,167 / −288 |
| 23 Oct | `dfa8bc9` | Tamu passes by email only, clearer IC/passport choice | 19 | +327 / −91 |
| 23 Oct | `f983e22` | Sign-in timeouts by role | 22 | +527 / −30 |
| 23 Oct | `62b7538` | Development mode only on local addresses | 6 | +60 / −4 |
| 23 Oct | `145846a` | Docker: pass Google Maps settings into the build | 1 | +3 |
| 23 Oct | `7c9a617` | Docker: include the public folder in hosted images | 1 | +1 |

The file and line columns are from `git log --shortstat` and include generated files, so they are larger than the totals at the top.

## Skills shown

TypeScript · Next.js 16 (App Router) · React 19 · PostgreSQL (triggers, constraints,
migrations, concurrency) · REST API design and OpenAPI · authentication and session security ·
OpenID Connect · applied cryptography (AES-GCM, HMAC, scrypt) · Redis · AI agents with tool
calling · Docker · GitHub Actions CI/CD · Vitest · accessibility (WCAG 2.2) · internationalisation ·
technical writing · leading a multi-person Git workflow.
