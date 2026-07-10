# Anna Setu — Food Waste Reduction Platform

A live demo built for **Smart India Hackathon** — problem statement *"Smart Management of Food Storage and Waste Reduction."*

Anna Setu connects anyone with surplus food (restaurants, hostels, event halls, households) to nearby NGOs/volunteers who can pick it up before it spoils.

This is a single static HTML file — no build step, no server to run — but it's now backed by a **real Firebase database**, so listings, claims and the ledger totals sync live across every visitor, from any device, permanently.

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

## 🔥 Firebase backend (already wired in)

Your `anna-food-reduction-platform` Firebase project is connected directly inside `index.html`:

- **Authentication** — email/password sign-in, via the "Sign in" button in the nav. Anyone must be signed in to post a listing or claim one; browsing the board is open to everyone.
- **Firestore** — two collections:
  - `listings` — every open surplus-food post. Deleted the moment it's claimed.
  - `claims` — one record per completed pickup, used to total up the "Meals rescued," "Waste diverted," and "CO₂e avoided" stats at the bottom of the demo.
- **Live sync** — the board, the ledger totals, and every visitor's view update in real time (via `onSnapshot`) with no page refresh needed.
- The five sample listings are seeded into Firestore automatically the very first time anyone loads the page on an empty database, so the board isn't empty before real users start posting.

### ⚠️ Before you demo or submit: lock down your Firestore rules

Your database is currently in **test mode**, which means anyone can read *and write* to it without restriction — fine for a hackathon demo, but it expires automatically after 30 days and isn't safe long-term. In the Firebase console → **Firestore Database → Rules**, replace the default rules with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /listings/{listingId} {
      allow read: if true;
      allow create: if request.auth != null;
      allow delete: if request.auth != null;
      allow update: if false;
    }
    match /claims/{claimId} {
      allow read: if true;
      allow create: if request.auth != null;
      allow update, delete: if false;
    }
  }
}
```

This keeps the board publicly viewable, but only signed-in users can post a listing, claim one, or log a rescue — and nobody can tamper with past records. Click **Publish** after pasting it in.

## 📝 Notes for your SIH submission

- The file **must be named `index.html`** and sit at the root of the repo (not inside a subfolder) — GitHub Pages looks for it there by default.
- Every time you push a change to `main`, the live link auto-updates in about a minute.
- Your Firebase web config is embedded directly in the page — that's expected and safe; Firebase web API keys aren't secret, they just identify your project, and the Firestore rules above are what actually control access.
- Good talking points for judges: real-time cross-device sync, authenticated donors/NGOs, and a public rescue ledger local bodies could use as waste-reduction policy data.
