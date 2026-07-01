<div align="center">

# Franciscus

**A digital portal for the Franciscan source texts.**

The early biographies of Francis of Assisi — in the original medieval Latin,
with translations, full-text search, and thematic cross-references — as a fast,
offline-capable web app, built on open data and open code.

[**▶ Open the app — franciscus.app**](https://franciscus.app)

[![Live](https://img.shields.io/badge/live-franciscus.app-green)](https://franciscus.app)
[![App: AGPL-3.0](https://img.shields.io/badge/app-AGPL--3.0-blue)](https://github.com/FranciscusApp/franciscus)
[![Corpus: CC0-1.0](https://img.shields.io/badge/corpus-CC0--1.0-lightgrey)](https://github.com/FranciscusApp/franciscus-data)

</div>

---

## What Franciscus is

Franciscus collects the **early sources for the life of Francis of Assisi** and
makes them genuinely readable on the web — searchable, deep-linkable, and
annotated, without ever losing the original Latin. It is free to read, free to
reuse, and free of a backend: the whole site is static, and the corpus travels
as portable, public-domain files.

The project is split across three repositories so each part can be used on its
own — read the texts as data, run the pipeline, or hack on the app.

## The repositories

| Repo | What it is | License |
|---|---|---|
| **[franciscus](https://github.com/FranciscusApp/franciscus)** | The application — a Rust CLI that compiles the corpus into a single SQLite/FTS5 database, plus a SvelteKit SPA that queries it entirely in the browser (`sql.js`/WASM). Deploys to GitHub Pages with no read-path server. | AGPL-3.0-or-later |
| **[franciscus-data](https://github.com/FranciscusApp/franciscus-data)** | The source corpus — medieval Latin texts, translations, semantic annotations, and topic pages, as plain Markdown + YAML. Portable and reusable on its own. | CC0-1.0 |
| **[franciscus-scripts](https://github.com/FranciscusApp/franciscus-scripts)** | The ingestion pipeline — Python tools that turn reference-edition PDFs into spec-compliant Markdown, plus AI-assisted translation and annotation. | AGPL-3.0 |

They fit together as a one-way flow:

```
PDFs ──[franciscus-scripts]──▶ franciscus-data (Markdown + YAML)
                                        │
                          [franciscus]  │  Rust CLI → franciscus.db (SQLite + FTS5)
                                        ▼
                               franciscus.app  ── static SPA, queries the DB
                                                  in-browser via sql.js (WASM)
```

## The corpus

| ID | Work | Author |
|----|------|--------|
| **1Cel** | Vita Prima | Thomas of Celano |
| **2Cel** | Vita Secunda | Thomas of Celano |
| **LMj** | Legenda Maior | Bonaventure |
| **3Soc** | Legenda Trium Sociorum | The Three Companions |
| **Testamentum** | Testamentum Sancti Francisci | Francis of Assisi |

Each work is available in the original **Latin** and an **Italian** translation,
with a reading interface in English or Italian; English translations are planned.

## What you can do with it

- 📖 **Read** each work chapter by chapter in Latin, Italian, or English.
- 🔎 **Search** the whole corpus full-text and jump straight to the passage.
- 🏷️ **Follow themes** — virtues, persons, places, and events get topic pages
  that gather every relevant passage across all the works.
- 🔗 **Link deeply** — every paragraph and verse has a stable, shareable URL.
- 📱 **Go offline** — it installs as a PWA and caches the database after the first visit.
- 🧩 **Reuse the data** — the corpus is CC0, so you can take it anywhere.

## Licensing

Two licences, deliberately:

- **Code** (`franciscus`, `franciscus-scripts`): **AGPL-3.0** — the application
  stays free, and every modified version must stay free with its source available.
- **Corpus** (`franciscus-data`): **CC0-1.0** — dedicated to the public domain,
  with no rights reserved. The medieval Latin is long out of copyright; CC0 also
  covers the editorial layer (encoding, IDs, annotations, topic pages, translations)
  so those are unambiguously free to reuse too.

## A note on AI

We are upfront about how the corpus was made. The **Latin texts** are
transcriptions of real public-domain print editions (chiefly the Quaracchi
*Analecta Franciscana*), machine-assisted but not AI-generated. The
**translations** and **annotations** are largely **machine-generated and not yet
fully human-reviewed**, so expect occasional errors. Treat Franciscus as a
reading and discovery tool, **not** a critical edition — and reporting mistakes
genuinely helps. Details live in each repo's README.

## Contributing

Corrections to the texts, translations, annotations, and code are all welcome —
this is exactly the kind of work that benefits from many eyes. Start from the
`CONTRIBUTING.md` in the relevant repo:
[app & pipeline](https://github.com/FranciscusApp/franciscus/blob/master/CONTRIBUTING.md)
·
[corpus](https://github.com/FranciscusApp/franciscus-data/blob/master/CONTRIBUTING.md).

## Get in touch

<div align="center">

<a href="https://verbumcaro.it"><img src="https://raw.githubusercontent.com/FranciscusApp/franciscus/refs/heads/master/app/static/vc-inline-dark.png" alt="Verbum Caro" width="240"></a>

</div>

A **Verbum Caro** project. Questions, corrections, or collaboration —
reach us at [info@verbumcaro.it](mailto:info@verbumcaro.it).
