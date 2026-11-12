# 🚀 SETUP GUIDE — DangerFuzail Advanced Profile Package

This package upgrades your GitHub profile README into an advanced, self-updating one.
Everything below takes about **10 minutes**.

## 📦 What's inside

```
DangerFuzail-profile/
├── README.md                              ← your new profile README (paste into DangerFuzail/DangerFuzail)
├── SETUP.md                               ← this guide
├── .github/
│   └── workflows/
│       ├── contribution-games.yml         ← generates Snake / Pac-Man / Breakout / Bomberman SVGs daily
│       └── blog-posts.yml                 ← auto-lists your latest dev.to posts in the README
├── arcade/
│   └── index.html                         ← playable Snake + Maze Chase (keyboard + touch)
└── game.html                              ← playable Neon Target Rush (mouse + touch)
```

## 1️⃣ Replace the placeholders in README.md

Search README.md for these and swap in your real values:

| Placeholder | Where | Replace with |
|---|---|---|
| `YOUR_LINKEDIN` | Connect With Me | your LinkedIn username |
| `YOUR_CHANNEL` | Connect With Me | your YouTube handle |
| `YOUR_USERNAME` (×2) | Connect With Me | your X / Instagram username |
| `YOUR_TELEGRAM` | Connect With Me | your Telegram username |
| `YOUR_BMC` (×2) | Support My Work | your Buy Me a Coffee slug |
| `ShopStack` / `TaskFlow API` / `DevBoard` | Featured Projects | your real repos (table **and** the 3 pin-card URLs) |

> Skill percentages in *Skill Progress* are editable shields badges — tune them freely.

## 2️⃣ Add the files to your profile repository

Upload everything to `https://github.com/DangerFuzail/DangerFuzail` (the special repo whose
README shows on your profile):

- `README.md` → repo root (replaces the old one)
- `.github/workflows/contribution-games.yml` and `blog-posts.yml`
- `arcade/index.html`
- `game.html`

Easiest way: drag-and-drop the folders on github.com (the web uploader accepts dot-folders),
or via git:

```bash
git clone https://github.com/DangerFuzail/DangerFuzail
cd DangerFuzail
# copy README.md, arcade/, game.html, .github/ from this package into the repo
git add .
git commit -m "Advanced profile: arcade games, auto workflows, new sections"
git push
```

## 3️⃣ Run the arcade workflow once

1. Open **Actions** tab → **Update arcade contribution animations**
2. Click **Run workflow** → **Run workflow** (green button)
3. Wait ~1–2 minutes. A new branch named `output` appears containing:
   `github-snake.svg`, `pacman-contribution-graph.svg`, `breakout-contribution-graph.svg`,
   `bomberman-contribution-graph.svg`, `snake-contribution-graph.svg` (+ dark variants).
4. Reload your profile → animations appear. They refresh **daily at 00:00 UTC** automatically
   (and on every push to main).

> 💡 If the games look dim on your screen, nothing is broken — the README ships light **and**
> dark SVG variants and GitHub auto-picks the right one.

## 4️⃣ Run the blog workflow once

1. Actions → **Latest blog posts** → Run workflow
2. The *Latest Blog Posts* section fills with your 4 newest dev.to articles.
3. Every new dev.to post appears automatically within 24 h (cron 03:00 UTC), or trigger it manually.

> Not on dev.to? Edit `blog-posts.yml` → `feed_list:` — a Medium and a Hashnode example
> URL are written as comments inside the file.

## 5️⃣ Enable GitHub Pages (activates the game links)

1. Settings → **Pages**
2. Source: **Deploy from a branch** → Branch: `main` → Folder: `/ (root)` → Save
3. Wait 1–2 minutes, then test:
   - Snake + Maze arcade: `https://dangerfuzail.github.io/DangerFuzail/arcade/`
   - Neon Target Rush: `https://dangerfuzail.github.io/DangerFuzail/game.html`

> ℹ️ GitHub Pages runs Jekyll, which converts your `README.md` into the site's `index.html`
> — that's why the "back to profile" links in the games work out of the box.

## 6️⃣ Troubleshooting

| Symptom | Fix |
|---|---|
| Arcade images show broken/404 | The `output` branch doesn't exist yet → run the workflow once (step 3). |
| Actions failed with `permission denied` | Make sure the workflow files are unchanged (they set `permissions: contents: write`), and the repo **Actions** are enabled in Settings → Actions. |
| Pin cards say "repository not found" | Expected until you create those repos or swap in your real ones (step 1). |
| Blog section is empty | Run the workflow once; also confirm you have at least one dev.to post under the username `DangerFuzail`. |
| Game links 404 | GitHub Pages not enabled (step 5), or Pages still deploying. |
| Colors look off in dark mode | Nothing to fix — light/dark SVG switching is automatic via `<picture>` tags. |

## 7️⃣ Customization cheat-sheet

- **Typing lines** → edit the `lines=` parameter of the readme-typing-svg URL (use `+` for spaces, `%7C` for `|`).
- **Arcade games** → in `contribution-games.yml`, `games: 'pacman,breakout,bomberman,snake'` — remove what you don't want (and delete its block in the README).
- **Skill bars** → plain shields badges: change the percentage (`85%25` = 85 %) and color hex.
- **More games** → https://github.com/abozanona/pacman-contribution-graph also supports more game modes.
- **Footer wave colors** → the two `capsule-render` URLs at the top/bottom of README.md.

— Made with 💙 · **DangerFuzail**
