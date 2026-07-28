# Setup

## 1. Repo structure

Everything goes in the special profile repo `tanishqwork/tanishqwork` (public, default branch `main`):

```
tanishqwork/
├── README.md
├── assets/
│   ├── hero.svg
│   └── pipeline.svg
└── .github/
    └── workflows/
        └── snake.yml
```

## 2. Enable the snake animation

The snake image in the README points at a branch that doesn't exist yet:

`https://raw.githubusercontent.com/tanishqwork/tanishqwork/output/snake.svg`

To create it:

1. Push all files to `main`.
2. Repo → **Settings → Actions → General → Workflow permissions** → select **Read and write permissions** → Save.
3. Repo → **Actions** tab → *Generate contribution snake* → **Run workflow**.
4. After it finishes, an `output` branch appears containing `snake.svg`, and the image resolves.

It then refreshes automatically every 12 hours. If you'd rather skip it, delete the snake `<img>` line from section `04 // TELEMETRY`.

## 3. Known constraints on GitHub

- **No JS, no CSS, no `<style>`.** GitHub sanitizes profile READMEs. All motion here comes from SVG animation (SMIL), which survives sanitization.
- **Interactivity** = the `<details>` accordions in section `03`, plus links. That's the full extent of what GitHub permits.
- **Camo caching:** GitHub proxies images. If you edit `hero.svg`, the old version may persist for a few minutes. Force a refresh by bumping the URL: `./assets/hero.svg?v=2`.
- **Fonts:** SVGs loaded via `<img>` can't fetch webfonts, so the hero uses the system monospace stack. It renders consistently across platforms but won't be JetBrains Mono specifically.
- **Third-party cards** (stats, streak, activity graph, trophies) are rendered by community services on Vercel. They occasionally rate-limit and show a broken image. That's transient, not your config.

## 4. Things worth editing

- `assets/hero.svg` — the telemetry block on the right (`uptime`, `p95 latency`, `region`) is decorative. Swap in real numbers or replace with anything else.
- `assets/pipeline.svg` — the metrics strip along the bottom pulls from your résumé claims. Keep them accurate.
- The `const tanishq = {...}` block in the README is the fastest thing to keep current when your role changes.
