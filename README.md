# The Hand of Liahim — Tarot Reader

A single-file tarot web app, plus a Capacitor wrapper that builds the same source into native Android (and, later, iOS) apps.

**[Live demo →](https://liahim.tgmf.st/)**

## Features

- 5 spreads: Single Card, Three-Card, Celtic Cross, Horseshoe, Relationship
- Full 78-card deck with upright & reversed meanings
- Historical card visuals from Wikimedia Commons and Archive.org (Rider-Waite-Smith, Visconti-Sforza)
- Optional AI interpretation via Anthropic, OpenAI, or Gemini — or none at all
- Two deck systems: Rider-Waite-Smith and Thoth

## Repo layout

- `docs/` — the actual web app (`index.html` + assets). This one folder is both the GitHub Pages source *and* Capacitor's `webDir` — the same files serve the live website and get bundled into the native apps, no duplication.
- `android/` — the generated native Android project (via Capacitor). Build output and machine-specific files are gitignored; the project itself is committed.
- `capacitor.config.json`, `package.json` — Node/Capacitor tooling used only to produce native builds. The website itself still has no backend, no dependencies, and no build step of its own — this tooling exists purely for the app wrapper.

## Deploy (website)

```bash
git clone https://github.com/tgmf/hand-of-liahim
cd hand-of-liahim/docs
# open index.html in a browser, or push to GitHub Pages (source: /docs, custom domain: liahim.tgmf.st)
```

## Build (mobile app)

```bash
npm install
npx cap sync android
npx cap run android      # or open android/ in Android Studio
```

Package ID: `st.tgmf.liahim`. Targeting Google Play first; iOS via `@capacitor/ios` is planned on the same codebase, no separate project.

## AI Keys

Keys are entered in-browser and never leave your device — they go directly to the provider's API and are cleared when the tab closes.

## License

Public domain. Do whatever you want with it.