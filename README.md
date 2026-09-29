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

### [StockLink — wholesale stock, from warehouse to shop door](https://github.com/MooketsiMagwaza/stocklink)

<a href="https://github.com/MooketsiMagwaza/stocklink">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/stocklink/stocklink-store-order-dark.png" alt="StockLink retail store view in dark mode, in a Mac window: an order in transit, with its delivery code, QR code and live position" width="100%">
</a>

<p align="center">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/stocklink/stocklink-driver-phones-dark.png" alt="StockLink driver app in dark mode, on two iPhones: collecting a parcel with the warehouse's pickup code, then on the road with the handover form" width="76%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/stocklink/stocklink-public-tracking-dark.png" alt="StockLink public tracking page in dark mode, in a Mac window: a parcel's journey and rounded position, no account needed" width="46%">
</p>

<sub>Dark mode, from StockLink's sample-data preview. The shops, orders and numbers are made up, and every page says so. The last window is the public tracking page, which anyone can open without an account.</sub>

Small shops often buy from several warehouses and then wait on deliveries they
can't see. I built StockLink to put all of that in one place. A shop orders from
many warehouses in one cart, demand from several shops can be pooled into one bulk
order, and every parcel can be followed from the warehouse door to the shop.
Prices are always worked out on the server, so the browser can't quietly change
what something costs.

- **How it's put together.** Five Rust (Axum) services, each with its own
  PostgreSQL database, sit behind one nginx gateway: identity, commerce,
  notifications, media and ops. Each service checks sign-in tokens on its own,
  Redis handles the denylist and the rate limits, and the services only talk to
  each other through internal APIs.
- **Who it's for.** One React app covers warehouses, shops, delivery drivers
  (built phone-first) and staff. It has light and dark themes, printable QR
  receipts and charts you can change.
- **Handing over a parcel.** Every delivery has two six-digit codes. The warehouse
  sees the pickup code and the shop sees the delivery code, so a driver can't
  collect or hand over a parcel without them. Anyone can follow a parcel from its
  tracking link, but they only see where it is, rounded to about 100 metres, never
  names, addresses or what's inside.
- **Keeping an eye on it.** Staff get an admin console inside the app: accounts,
  sessions, API keys, a read-only database viewer that hides secret columns,
  support tickets and an audit log. It sits next to Prometheus and Grafana, and
  Grafana links back to it.
- **One look everywhere.** The app, the docs site and the marketing site all use
  the same Apple-inspired design, built from one set of tokens.
- **What isn't done.** I'd rather say it than hide it. The screenshots come from a
  sample-data preview, I haven't yet brought the whole Docker stack up end to end
  or run the newest migrations on a real database, and the event outbox and Kafka
  publisher aren't finished.

**Core stack:** Rust · Axum · sqlx · PostgreSQL · Redis · React · TypeScript ·
Docker · nginx · Prometheus · Grafana

### [Tsela — Gaborone transit, made searchable](https://github.com/MooketsiMagwaza/transit-route-optimization)

<a href="https://github.com/MooketsiMagwaza/transit-route-optimization">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/tsela/tsela-surfaces.png" alt="Tsela's four surfaces in Mac windows: the rider app exploring every route, the marketing site, the admin dashboard, and the developer portal's API console" width="100%">
</a>

Tsela turns Gaborone's informal combi knowledge into a route-planning platform.
A rider can choose an origin and destination, compare road-following routes, see
where to board, and understand where to get off. The same repository includes
the rider experience, marketing site, operations dashboard, authenticated
developer portal, and API.

- FastAPI owns the HTTP API; PostgreSQL, PostGIS, and pgRouting own spatial data
  and road-aligned routing; OR-Tools supports optimization work.
- Five separate product surfaces share one platform without collapsing into one
  monolithic application.
- Prometheus, Grafana, Tempo, OpenTelemetry, structured logs, and request IDs
  provide an observable path through the system.
- The repository documents security boundaries, backups and recovery, production
  authentication, data ownership, API limits, accessibility, and launch gaps.

**Core stack:** Python · FastAPI · PostgreSQL · PostGIS · pgRouting · Next.js ·
TypeScript · Docker · Prometheus · Grafana

### [Obsidian Sync for iOS — local-first vault synchronization](https://github.com/MooketsiMagwaza/obsidian-sync-ios)

<a href="https://github.com/MooketsiMagwaza/obsidian-sync-ios">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/obsidian-sync-ios/main/docs/images/vault-sync-active-session.jpg" alt="Obsidian Sync transferring an established vault on a physical iPad" width="100%">
</a>

A free, open-source iPhone and iPad companion that joins an existing Syncthing
cluster and synchronizes an Obsidian vault without a hosted account or proprietary
sync service.

- A narrow Go/Swift boundary embeds the real Syncthing engine inside a native
  SwiftUI application.
- Physical testing proved desktop-to-iPad and iPad-to-desktop transfers, including
  a deletion propagated back to the desktop.
- GitHub Actions cross-compiles the XCFramework, builds the iOS app, runs the
  linked simulator suite, and publishes an unsigned device IPA.
- The README clearly labels it a foreground-only development release and documents
  backups, signing, conflict, permission, and long-session risks.

**Core stack:** Go · Swift · SwiftUI · Syncthing · GitHub Actions

## Other technical work

| Project | Why it exists |
| --- | --- |
| [University CS Docs](https://university-cs-docs.vercel.app) | A deployed, open-source learning platform for University of Botswana computer-science courses, backed by CI, CodeQL, and reusable interactive MDX components. |
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

- **StockLink:** get the whole stack running on Docker for the first time, then
  finish event delivery.
- **Tsela:** check the route data against real Gaborone roads and what riders
  actually know, and move sign-in and ops controls from local demos to something
  ready to launch.
- **Obsidian Sync for iOS:** keep pushing on interrupted transfers, conflicts,
  permissions and bigger vaults.

## Let's talk

I am interested in teams that care about product thinking, dependable backend
systems, and engineers who can work across boundaries. I am especially happy to
walk through the decisions, trade-offs, and unfinished edges in any project
above.

**[mooketsimagwazajr@gmail.com](mailto:mooketsimagwazajr@gmail.com)**
