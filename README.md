# Anna Setu — Food Waste Reduction Platform

A live demo built for **Smart India Hackathon** — problem statement *"Smart Management of Food Storage and Waste Reduction."*

Anna Setu connects anyone with surplus food (restaurants, hostels, event halls, households) to nearby NGOs/volunteers who can pick it up before it spoils.

This is a single static HTML file — no backend, no build step, no dependencies to install. It runs entirely in the browser.

## 🔗 Live site

Once deployed (steps below), your site will be live permanently at:

```
https://<your-github-username>.github.io/<repo-name>/
```

## 🚀 How to publish this on GitHub Pages (takes ~2 minutes)

**Option A — using the GitHub website (no coding tools needed)**

1. Go to [github.com](https://github.com) and log in (create a free account if you don't have one).
2. Click the **+** icon top-right → **New repository**.
3. Name it something like `anna-setu-food-waste`. Keep it **Public**. Click **Create repository**.
4. On the new repo page, click **"uploading an existing file"** (or Add file → Upload files).
5. Drag in `index.html` from this folder. Click **Commit changes**.
6. Go to the repo's **Settings** tab → **Pages** (left sidebar).
7. Under "Build and deployment" → Source, select **Deploy from a branch**.
8. Branch: `main`, folder: `/ (root)`. Click **Save**.
9. Wait ~1 minute, then refresh — GitHub shows your live URL at the top of that Pages settings screen:
   `https://<your-username>.github.io/anna-setu-food-waste/`

That link works forever, any time, on any device — GitHub hosts it for free.

**Option B — using git from a terminal**

```bash
git init
git add index.html README.md
git commit -m "Anna Setu - food waste reduction platform"
git branch -M main
git remote add origin https://github.com/<your-username>/anna-setu-food-waste.git
git push -u origin main
```

Then repeat steps 6–9 above to turn on Pages.

## 📝 Notes for your SIH submission

- The file **must be named `index.html`** and sit at the root of the repo (not inside a subfolder) — GitHub Pages looks for it there by default.
- Every time you push a change to `main`, the live link auto-updates in about a minute.
- This prototype runs all data in-memory in the browser (resets on refresh). For the next stage, mention that a real deployment would add a backend (Firebase/Node) so listings persist and NGOs can be verified — good talking point for judges on your roadmap slide.
