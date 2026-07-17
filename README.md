# Data Viewer

A fast, mobile-first, **single-file** data viewer. Drag & drop a JSON, YAML,
CSV, or XML file anywhere on the page and explore it as a **collapsible tree**
or a **table** — one tap flips to the syntax-highlighted **source**. It's a
**viewer, not an editor** — no toolbars, no accounts, no uploads. Everything
runs locally in your browser.

🔗 **Live:** <https://data-viewer.us/>

![Single file](https://img.shields.io/badge/build-single%20HTML%20file-success) ![No build step](https://img.shields.io/badge/build%20step-none-success) ![License](https://img.shields.io/badge/license-MIT-blue)

> Part of the **[File Viewer](https://file-viewer.us/) family** — HTML, Markdown,
> ePUB, PDF, and Data each have their own dedicated viewer. Use the **☰ menu**
> in the header to jump between them.

## Features

- 🌳 **Tree view** — JSON, JSONC, JSON5, JSON-LD, NDJSON, and YAML parse into a
  **collapsible, type-colored tree** with key/item counts.
- 📊 **Table view** — CSV and TSV render as a **table** (sticky header, zebra
  rows, quoted-field aware).
- 🧬 **XML view** — XML, RSS, and ATOM render as a collapsible element tree.
- `</>` **Source view** — every file also has a syntax-highlighted, line-numbered
  source view. TOML and GraphQL open straight into it.
- ✨ **Format** — a `{ }` toggle pretty-prints the raw source (JSON, NDJSON,
  YAML, XML) — great for minified data — and flips back to raw.
- 🔀 **Drop to replace** — drop a new file while one is open and it replaces the
  current view (drag & drop anywhere, or paste).
- ☰ **Family menu** — a hamburger flyout links to every viewer (Home, HTML,
  Markdown, ePUB, Data, PDF).
- ✅ **File-type checking** — only data types are accepted; other files are
  politely declined so you land in the right viewer.
- 🎨 **Pick any background color** — text, borders, and syntax colors adapt for
  contrast (light **and** dark), remembered across visits.
- 🫥 **Distraction-free** — the header hides on scroll-down and returns on
  scroll-up, after 5 s, or at the top edge; the footer has a **×** to hide it.
- 📱 **Mobile-first**, safe-area aware, keyboard-accessible.
- 🪶 **One file, no build** — `index.html` is self-contained (~240 KB, libraries
  inline) and works offline, even from `file://`.
- 📊 **Privacy-friendly analytics** — self-hosted, cookieless
  [Plausible](https://plausible.io/); your files never leave your device.

## Supported file types

| View | Types |
| --- | --- |
| **Tree** | `.json` `.jsonc` `.json5` `.jsonld` `.ndjson` `.yaml` `.yml` |
| **Table** | `.csv` `.tsv` |
| **XML tree** | `.xml` `.rss` `.atom` |
| **Source only** | `.toml` `.graphql` `.gql` |

Any other type is declined with a brief notice. A file that fails to parse
falls back to the source view automatically.

## Quick start

**Just open it.** Download [`index.html`](index.html), double-click it — no
server, no build, no internet needed. Prefer a local server?

```sh
python3 -m http.server 8080   # then open http://localhost:8080
```

## Deploy to Cloudflare Pages

Connect the repo (**Workers & Pages → Create → Pages → Connect to Git**),
framework preset **None**, build command blank, output directory `/`. The
[`_headers`](_headers) file applies a strict CSP automatically. Add the custom
domain **data-viewer.us** under the project's Custom domains tab.

## How it works

Everything is in [`index.html`](index.html) — app logic plus three inline
libraries, so parsing, highlighting, and formatting all work offline:

- [**highlight.js**](https://github.com/highlightjs/highlight.js) `v11.9.0`
  (BSD-3-Clause) — source-view syntax highlighting.
- [**js-yaml**](https://github.com/nodeca/js-yaml) `v4.1.0` (MIT) — YAML
  parsing and formatting.
- [**JSON5**](https://github.com/json5/json5) `v2.2.3` (MIT) — JSON5 parsing.

The tree, table, and XML views are built as escaped DOM (never `innerHTML` of
untrusted text), and the viewer never renders arbitrary HTML — so its CSP is
strict (`default-src 'none'`, no external assets).

## Credits

| Component | Version | License |
| --- | --- | --- |
| [highlight.js](https://github.com/highlightjs/highlight.js) | 11.9.0 | BSD-3-Clause |
| [js-yaml](https://github.com/nodeca/js-yaml) | 4.1.0 | MIT |
| [JSON5](https://github.com/json5/json5) | 2.2.3 | MIT |
| [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono) | 2.305 (subset) | SIL OFL-1.1 |

The file-type icon (favicon and header icon) is from
[vscode-icons](https://github.com/vscode-icons/vscode-icons) (MIT). Analytics by
[Plausible](https://plausible.io/).

## License

[MIT](LICENSE) © 2026 Michal Ferber, aka **TechGuyWithABeard**. Bundled
components retain their own licenses — see [`LICENSE`](LICENSE) and
[Credits](#credits).
