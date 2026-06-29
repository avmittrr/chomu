# Chomu

A tiny one-page web app: tap a button, hear a funny voice say "I'm a chomu"
or "I'm a mundu". Built for an iPhone.

## What's here
- `index.html` — the entire app. Self-contained: HTML + CSS + JS + two voice
  clips embedded as base64 MP3. No build, no dependencies, works offline once
  loaded. (Full deploy instructions are also in a comment at the top of the
  file.)

## Claude: how to deploy it
1. Put `index.html` at the repo root (it's already named for that) and push to
   `main`.
2. Turn on GitHub Pages — repo is public, so:
   **Settings -> Pages -> Source = "Deploy from a branch", Branch = `main`,
   Folder = `/` (root) -> Save.**
   Only the repo owner can flip this switch; an integration token cannot
   (`Resource not accessible by integration`). If you hit that, ask the owner
   to toggle it, then carry on.
3. Live at `https://<owner>.github.io/<repo>/` (e.g.
   `https://avmittrr.github.io/chomu/`) after ~1-3 min.

## Important (don't break these)
- Sound uses the **Web Audio API** (decodes the embedded MP3) because that
  **ignores the iPhone silent switch**. Do **not** make `speechSynthesis` the
  primary path — iOS mutes it on silent mode and it fails in `data:` URLs.
- Must be served over **http(s)**; local files / `data:` URLs don't run
  reliably on iOS Safari.
- On the phone: volume up, tap a button — works even on silent.
