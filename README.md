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

### [Zenith — time tracking with intention](https://github.com/MooketsiMagwaza/Zenith)

<a href="https://github.com/MooketsiMagwaza/Zenith">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/zenith/zenith-decks.webp" alt="Zenith's decks view on a black canvas: a deck called Academics with three timed cards for a study session, a lab, and practice" width="100%">
</a>

<p align="center">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/zenith/zenith-journal.webp" alt="Zenith's markdown journal, one document per card or deck" width="76%">
</p>

Most productivity apps are built to capture tasks or to bill time. Zenith is built
for attention: pick one card, run a session, and write down what happened. A
deliberate-practice timer, a deck and card workspace, a markdown journal,
reminders, and a full-screen Zen mode share one quiet, dark surface.

- **Open source.** MIT licensed. One repository holds the React app (which runs in
  a browser and, wrapped in Tauri, on the desktop), a small always-on-top Tauri
  pop-up, a marketing site, and the sync engine described below.
- **Local-first.** State lives on your device. There is no server and no account.
- **One target, one document.** Every card and every deck has exactly one journal,
  and the data layer enforces it.
- **Recoverable.** Every delete returns an undo handle, including a deck with its
  cards and their journals.
- **Optional progress.** Targets per card or deck and progress bars are built and
  switched off by default.
- **Sync without an account (in progress).** Devices on one network will pair once
  with a code and keep their data in step. The library is written and tested on one
  machine: device identity, a change store, a merge model chosen by measuring
  Automerge against Yjs, SPAKE2 pairing, and a pinned mutual-TLS transport. It is not
  in the app yet and has had no independent security review.
- **Honest status.** Nobody has opened the desktop window yet, and the sync has
  never run across two real machines.

**Core stack:** React · TypeScript · TanStack · Tailwind CSS · Tauri 2 · Rust

### Kori — an offline-first safari and wildlife app for Botswana

*In development. The repository is private for now.*

Named after the kori bustard, Botswana's national bird. The aim: log a sighting with
no mobile signal, download park maps before the trip, and be guided to a sighting
along existing roads and tracks.

- **Safety and privacy first.** No live animal locations: others see a sighting only
  after review and a delay, as an area. Sensitive species are shown coarsely and are
  never guided to. GPS trip recording is opt-in.
- **Built so far.** Four web apps on sample data: a phone-first field app (logging a
  sighting on the phone's own storage, a sample park map drawn without any tiles,
  routing along tracks, and QR codes that share a sighting), a landing site, a
  review console, and an API docs site.
- **A backend, not connected yet.** A Python service (FastAPI, PostGIS, migrations,
  tests) with accounts, scoped API keys, review, uploads, and an audit log, and a
  Docker stack with monitoring and backups. The apps do not call it yet.
- **Honest status.** The park in it is fictional sample data. It is not deployed, it
  has not been tried on a real phone, and no real park maps exist yet.

**Core stack:** Next.js · TypeScript · MapLibre · Python · FastAPI · PostGIS

### Tagwise — a shared register for an organisation's assets and stock

*In development. The repository is private for now.*

For schools, clinics, offices, and stores that keep their register in a spreadsheet.
The aim: scan QR codes and barcodes in the browser, count stock together, bring in
Excel and CSV files, and see sites on a map.

- **Built so far, in a browser prototype.** A register table with saved views, asset
  pages with comments and history, printable QR label sheets, scanning with a
  manual-entry fallback, an Excel and CSV import wizard that checks each row, stock-takes,
  and a sites map.
- **A backend, not connected yet.** Rust services on Axum and PostgreSQL (identity,
  media, notifications, a register service), a Docker stack with an nginx gateway
  and monitoring, and a docs site. Unit tests and database tests run in CI. The app
  does not call the services yet.
- **Honest status.** It runs on a sample workspace in the browser's own storage.
  Camera scanning has not been tried on a real phone, and it is not deployed.

**Core stack:** React · TypeScript · Vite · Rust · Axum · PostgreSQL

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

- **Zenith:** put the sync engine inside the app (a Devices screen and the desktop integration), run it across two real machines, and have the transport reviewed by someone independent. Then finish the companion messages, rewards, Pomodoro, calendar, and open data formats.
- **Kori and Tagwise:** connect each app to its backend, deploy both, try scanning and the maps on real phones, and review the code before making either repository public.

## Let's talk

I am interested in teams that care about product thinking, dependable backend
systems, and engineers who can work across boundaries. I am especially happy to
walk through the decisions, trade-offs, and unfinished edges in any project
above.

**[mooketsimagwazajr@gmail.com](mailto:mooketsimagwazajr@gmail.com)**
