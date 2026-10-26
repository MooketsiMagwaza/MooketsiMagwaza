# Mooketsi Vincent Magwaza

### Full-stack engineer building useful products and the systems that keep them running

I turn early ideas into working software: the interface, API, data model,
authentication, documentation, deployment path, and operational tooling. I care
about products that solve real problems, especially where local knowledge or
everyday workflows have not yet been made easy to use.

Based in **Gaborone, Botswana**. Open to backend, full-stack, and platform-focused
opportunities.

[Portfolio](https://mooketsimagwaza.github.io/portfolio/) ·
[Email me](mailto:mooketsimagwazajr@gmail.com) ·
[View my repositories](https://github.com/MooketsiMagwaza?tab=repositories)

---

## What I build

- **Product systems** — web and mobile experiences designed around a real user
  journey, not a collection of disconnected screens.
- **Backend and data platforms** — domain-focused APIs, spatial data, queues,
  caching, authentication, and databases with explicit ownership.
- **Production foundations** — observability, rate limits, security boundaries,
  recovery documentation, and deployment workflows that make a system operable.

## Selected work

### [Kori — an offline-first safari and wildlife app for Botswana](https://github.com/MooketsiMagwaza/kori)

<table>
  <tr>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/kori/kori-landing.webp" alt="The Kori landing page: a headline about wildlife sightings that keep working where the signal ends, with a phone showing a route along tracks" width="100%"></td>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/kori/kori-review.webp" alt="The Kori review console: a queue of waiting sightings with a map of the selected sighting's one-kilometre area" width="100%"></td>
  </tr>
  <tr>
    <td colspan="2"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/kori/kori-phones.webp" alt="Three phones showing the Kori field app: the home screen, the offline map with sighting markers and tracks, and the form for logging a sighting" width="100%"></td>
  </tr>
</table>

Named after the kori bustard, Botswana's national bird. Log a sighting with no mobile
signal, download park maps before the trip, and be guided to a sighting along existing
roads and tracks. The park shown is a fictional sample reserve.

- **Safety and privacy by design.** No live animal locations: others see a sighting only
  after review and a delay, as an area. Sensitive species are shown coarsely and are
  never guided to. GPS trip recording is opt-in per trip, trimmed, delayed, and deletable.
- **Four web apps.** A phone-first field app (an IndexedDB outbox, a downloaded park pack
  drawn with MapLibre without any tiles, routing along tracks only, QR share and scan), a
  landing site, a review console, and an API docs site generated from the service's
  OpenAPI document.
- **A real backend.** A Python service with accounts, scoped API keys and quotas,
  throttling, an audit log, uploads, a review flow, trips and a track map, and 13 database
  migrations on PostGIS. It has 93 passing tests and runs in CI against a PostGIS service.
  The apps do not call it yet, so the data in them stays on the device.
- **Operations included.** Backups, a standby and a restore drill, monitoring
  dashboards, tracing, and a Trivy and dependency-audit workflow.

| Layer | What it uses |
| --- | --- |
| Front end | Next.js 16, React 19, TypeScript, MapLibre, IndexedDB, jsQR |
| API | Python 3.12, FastAPI, SQLAlchemy 2, GeoAlchemy2, Alembic, a scheduler |
| Auth and files | GoTrue (an open-source auth server), MinIO object storage |
| Data | PostgreSQL 16 with PostGIS, a standby, scheduled backups, a restore drill |
| Observability | OpenTelemetry, Prometheus, Grafana, Tempo, a Postgres exporter |
| Delivery | Docker Compose, GitHub Actions, Trivy, Dependabot |

### [Tagwise — a shared register for an organisation's assets and stock](https://github.com/MooketsiMagwaza/tagwise)

<table>
  <tr>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/tagwise/tagwise-home.webp" alt="The Tagwise home screen: items needing attention, recent activity, a stock-take in progress, and stock by site" width="100%"></td>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/tagwise/tagwise-register.webp" alt="The Tagwise register: a table of assets with saved views, filters, and status" width="100%"></td>
  </tr>
  <tr>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/tagwise/tagwise-asset.webp" alt="A Tagwise asset page with its details, custody, comments, and a printable QR label" width="100%"></td>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/tagwise/tagwise-import.webp" alt="The Tagwise import check: columns matched from an Excel file and the rows with problems listed" width="100%"></td>
  </tr>
  <tr>
    <td colspan="2"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/tagwise/tagwise-sites.webp" alt="The Tagwise sites map with a pin for each site" width="100%"></td>
  </tr>
</table>

For schools, clinics, offices, and stores that keep their register in a spreadsheet. Scan
QR codes and barcodes in the browser, print labels, count stock together, bring in Excel
and CSV files, and see sites on a map. The organisation shown is a fictional sample.

- **The register.** Saved views, filters and sorting, asset and stock pages with check-out,
  issue and receive, comments, history, and roles; edits made from an out-of-date copy open
  a conflict dialog instead of overwriting.
- **Scan and label.** Camera scanning with a manual-entry fallback, and printable QR label
  sheets.
- **Import and export.** An Excel and CSV import wizard that matches columns, checks every
  row, handles duplicates, and writes a problem report.
- **Stock-takes** several people can run at once, and a map of sites.
- **Five Rust services.** Identity, register, notifications, media, and ops, each with its
  own database and migrations, behind an nginx gateway. The register service's database
  tests (concurrent issues never take stock below zero, retries are idempotent, workspaces
  are isolated) run in CI on PostgreSQL, and a smoke test signs in by one-time code and
  checks that another account is refused. The app runs on a sample workspace in the browser
  and does not call the services yet.

| Layer | What it uses |
| --- | --- |
| Front end | React 18, TypeScript, Vite, MapLibre, ZXing, SheetJS |
| Services | Rust, Axum, tower; identity, register, notifications, media, ops |
| Gateway and runtime | nginx, Docker Compose |
| Data | PostgreSQL (a database per service), Redis |
| Observability | OpenTelemetry, Prometheus, Grafana, Tempo; a request ID in every log line |
| Docs | Fumadocs, with an OpenAPI reference generated from the services |
| Delivery | GitHub Actions (lint, type-check, tests, build, compose validation, database tests), Dependabot |

### [Zenith — time tracking with intention](https://github.com/MooketsiMagwaza/Zenith)

<table>
  <tr>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/zenith/zenith-decks.webp" alt="Zenith's decks view on a black canvas: a deck called Academics with three timed cards" width="100%"></td>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/zenith/zenith-journal.webp" alt="Zenith's markdown journal, one document per card or deck" width="100%"></td>
  </tr>
  <tr>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/zenith/zenith-history.webp" alt="Zenith's history of past focus sessions" width="100%"></td>
    <td width="50%"><img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/zenith/zenith-zen.webp" alt="Zenith's full-screen Zen mode" width="100%"></td>
  </tr>
</table>

Most productivity apps are built to capture tasks or to bill time. Zenith is built for
attention: pick one card, run a session, and write down what happened. A
deliberate-practice timer, a deck and card workspace, a markdown journal, reminders, and a
full-screen Zen mode share one quiet, dark surface.

- **Open source (MIT).** One repository holds the React app, which runs in a browser and,
  wrapped in Tauri, on the desktop; a small always-on-top Tauri pop-up with an opt-in
  desktop pet; a marketing site; and the sync engine.
- **Local-first.** State lives on your device. There is no server and no account.
- **One target, one document.** Every card and deck has exactly one journal, and the data
  layer enforces it. Every delete returns an undo handle.
- **Optional extras, off by default.** Goals and progress bars, companion messages
  ("time for…"), session recaps and affirmations, a Pomodoro timer, a calendar with
  iCalendar export, and versioned export and import in open formats (JSON, CSV, Markdown,
  iCalendar, with Toggl and Clockify CSV importers).
- **Sync without an account.** A Rust library gives each device its own identity and pairs
  devices once with a code (SPAKE2), then moves changes over mutual TLS with pinned
  certificates. Merging uses Automerge, chosen over Yjs by measuring both. It passes 36
  tests on one machine and is not in the app yet.

| Layer | What it uses |
| --- | --- |
| App | React, TypeScript, Vite, TanStack Router, Tailwind CSS |
| Desktop and pop-up | Tauri 2, Rust |
| Sync engine | Rust, SQLite, rustls, SPAKE2, Automerge, mDNS |
| Marketing site | React, TypeScript, Vite, prerendered to static HTML with no scripts |
| Delivery | npm workspaces and a Cargo workspace in one repository, Netlify |

## Other technical work

| Project | Why it exists |
| --- | --- |
| [University CS Docs](https://university-cs-docs.vercel.app) | A deployed, open-source learning platform for University of Botswana computer-science courses, backed by CI, CodeQL, and reusable interactive MDX components. |
| [Zenith Agent](https://github.com/MooketsiMagwaza/zenith-agent) | The earlier Electron prototype of Zenith as a floating desktop agent. Its successor is the Tauri pop-up inside the Zenith repository. |
| [GlassHID](https://github.com/MooketsiMagwaza/GlassHID) | Turns an Android phone into a local-only Bluetooth keyboard, trackpad, media remote, and gamepad using native HID APIs. |
| [Obsidian Excalidraw Low Latency](https://github.com/MooketsiMagwaza/obsidian-excalidraw-low-latency) | A low-latency pen companion for handwritten work in Obsidian Excalidraw. |

## Technical toolkit

| Area | Tools I use |
| --- | --- |
| Backend | Rust, Axum, Python, FastAPI, Go, Java, REST APIs |
| Web | TypeScript, React, Next.js, Vite, accessible responsive UI |
| Data | PostgreSQL, PostGIS, pgRouting, Redis, SQLAlchemy, sqlx, Alembic |
| Operations | Docker, nginx, GitHub Actions, Prometheus, Grafana, Tempo, OpenTelemetry |
| Native | Swift, SwiftUI, Android platform APIs, Bluetooth HID |

## How I work

1. Start with the user journey and the facts the system must preserve.
2. Give data and service boundaries explicit owners.
3. Treat authentication, validation, rate limits, and failure states as product
   work—not a cleanup phase.
4. Document what is working, what is scaffolded, and what evidence is still
   needed before launch.
5. Prefer a small, understandable system until measured load justifies more
   infrastructure.

## Next up

- **Kori and Tagwise:** connect each app to its backend, deploy both, try scanning and the maps on real phones, and have the code reviewed by someone independent. Kori is also getting a real offline map in place of its illustrated sample reserve.
- **Zenith:** put the sync engine inside the app, run it across two real machines, and have the transport reviewed by someone independent.

## Let's talk

I am interested in teams that care about product thinking, dependable backend
systems, and engineers who can work across boundaries. I am especially happy to
walk through the decisions, trade-offs, and unfinished edges in any project
above.

**[mooketsimagwazajr@gmail.com](mailto:mooketsimagwazajr@gmail.com)**
