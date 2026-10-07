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

- **Local-first.** State lives in the browser and the app loads as a static page.
  Optional accounts add sync across devices.
- **One target, one document.** Every card and every deck has exactly one journal,
  and the data layer enforces it.
- **Recoverable.** Every delete returns an undo handle, including a deck with its
  cards and their journals.
- **Keyboard-first where it matters.** Esc closes everything, and Cmd or Ctrl-click
  selects cards across decks.
- **Specified down to the key.** The README is the full specification: every
  screen, keystroke, storage key, and design token.

**Core stack:** React · TypeScript · TanStack · Tailwind CSS · Supabase (optional accounts)

### [Zenith Agent — time tracking as a resident desktop agent](https://github.com/MooketsiMagwaza/zenith-agent)

The Zenith idea as a floating desktop agent: a HUD layer, a command palette,
journaling, reminders, and a Zen surface in one frameless, transparent Electron
window that Alt+Space summons.

- **Local-first.** State stays on the machine, with no servers, no accounts, and
  no analytics.
- **Built like a native utility.** Frameless, always on top, and click-through
  where the window is transparent.
- **Layers kept apart.** The main process, the preload bridge, and the renderer
  are separate, with shared types in one place.
- **Honest status.** It is a work in progress that I am bringing back up to the
  standard of my other projects, and it has no screenshots yet.

**Core stack:** Electron · React · TypeScript · electron-vite · Tailwind CSS

### [Orb View — explore how ideas connect](https://github.com/MooketsiMagwaza/orb-view)

<a href="https://orb-view.vercel.app">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/orb-view/orb-view-library.webp" alt="The Orb View library: a search field, subject filters, and cards for Me and Engineering and Technology with their topics" width="100%">
</a>

<p align="center">
  <img src="https://raw.githubusercontent.com/MooketsiMagwaza/MooketsiMagwaza/main/assets/orb-view/orb-view-map.webp" alt="The Orb View concept map: Entropy at the centre with eight connected ideas around it" width="76%">
</p>

A visual learning app for seeing how ideas connect. Browse a library of concepts,
follow guided learning paths, or wander an open map one connection at a time.
[Try it live](https://orb-view.vercel.app).

- **Content as data.** Concepts, categories, learning paths, and cross-links are
  validated JSON, with checks for the data, the links, and the paths.
- **A docs site from the same source.** A separate Next.js and Fumadocs app
  publishes the whole library as browsable documentation.
- **Web and desktop.** The same app builds for the browser and as a Tauri 2
  desktop app.

**Core stack:** React · TypeScript · Vite · Tauri 2

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

- **Zenith Agent:** bring it back up to the standard of Zenith, with screenshots and
  a written note of what has and hasn't been tested.
- **Orb View:** write more concepts in depth and keep the content checks strict.
- **Obsidian Sync for iOS:** keep pushing on interrupted transfers, conflicts,
  permissions and bigger vaults.

## Let's talk

I am interested in teams that care about product thinking, dependable backend
systems, and engineers who can work across boundaries. I am especially happy to
walk through the decisions, trade-offs, and unfinished edges in any project
above.

**[mooketsimagwazajr@gmail.com](mailto:mooketsimagwazajr@gmail.com)**
