# Tour825.com — Deploy Guide

This folder is the whole site. It only needs three things to go live on GitHub Pages:

```
index.html      <- the page itself
images/         <- all 24 real photos it references
CNAME           <- tells GitHub Pages to serve this at tour825.com
```

## 1. Push it to GitHub

If you don't have a repo yet:

1. Create a new **public** repo on GitHub (e.g. `tour825`). Don't initialize it with a README.
2. From this folder, run:
   ```bash
   git init
   git add index.html images CNAME
   git commit -m "Launch Tour825.com"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

If you already have the repo cloned locally, just copy `index.html`, the `images/` folder, and `CNAME` into it, then `git add` / `commit` / `push` as usual.

## 2. Turn on GitHub Pages

In the repo: **Settings → Pages**
- Source: `Deploy from a branch`
- Branch: `main`, folder: `/ (root)`
- Save

GitHub will build the site at `https://<your-username>.github.io/<repo-name>/` within a minute or two — check that it looks right before moving to the domain step.

## 3. Point tour825.com at it

Since you already own the domain, add these records at your DNS provider (wherever you bought/manage tour825.com):

**Apex domain (tour825.com) — four A records:**
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**www subdomain (optional, recommended) — one CNAME record:**
```
www.tour825.com  →  <your-username>.github.io
```

DNS changes can take anywhere from a few minutes to a few hours to propagate.

Back in **Settings → Pages** on GitHub, enter `tour825.com` as the custom domain (the `CNAME` file already in this folder does this automatically once pushed, but the field should confirm it). Once GitHub verifies the DNS, check **Enforce HTTPS** — it may take a bit to become available after the domain first resolves.

## Before you call it fully live

A few things are still placeholders in the page — search `index.html` for `[` to find them:
- **Phone number** — currently `[Google Voice number — TBD]` in the footer.
- **Property taxes** — currently `[ Confirm current year ]` in the Details section.
- **Driveway photo** — the gallery has a "coming soon" card waiting for it.

The two "Contact Agent" / "Request Inspection Report" buttons already send real, pre-drafted emails to **Doug@Tour825.com** — worth double-checking that inbox is actually set up and being checked before launch.
