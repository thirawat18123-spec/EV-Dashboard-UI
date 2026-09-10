# EV Telemetry Dashboard — Static Prototype

Single-file dashboard (`index.html`, no build step, no dependencies except a
Google Fonts link) showing simulated live values for:

- Module temperatures (4x STM32 boards)
- Motor temperature
- Motor RPM
- Vehicle speed (km/hr)
- Energy consumption rate + session total (kW/hr, kWh)
- Battery level (%)
- Estimated range (km)
- System alerts (auto-generated from the simulated thresholds)

All data is randomly generated client-side in `<script>` — nothing is wired
to real hardware yet. Swap the `state`/`pickNewTargets()`/`tick()` logic in
the script for real serial/BLE/websocket reads when hardware is ready; every
DOM element already has an id `render()` writes to.

## Run locally
Just open `index.html` in a browser — no server needed.

## Push to GitHub (public repo)
```bash
git init
git add index.html README.md
git commit -m "EV telemetry dashboard prototype"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```
Make sure the repo visibility is set to **Public** when you create it on GitHub.

## Deploy — GitHub Pages (easiest, free)
1. On the repo page: **Settings → Pages**.
2. Under "Build and deployment", set **Source: Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)` → **Save**.
4. Wait ~1 minute; your live URL appears at the top of that page
   (`https://<your-username>.github.io/<repo-name>/`).

## Deploy — Vercel (alternative)
1. Go to vercel.com → **Add New Project** → import the GitHub repo.
2. Framework preset: **Other** (it's a static file, no build command needed).
3. Deploy — Vercel gives you a `*.vercel.app` URL immediately.
