# Rust Portfolio — Setup Guide

## Files in this repo

```
.
├── README.md                                  ← your GitHub profile page
├── index.html                                 ← standalone portfolio site (optional)
└── .github/workflows/update-rust-projects.yml ← auto-updates project table daily
```

---

## 1. Create the profile repo

On GitHub, create a **new public repo** with the name **exactly equal to your username**.
e.g. if your username is `ferris`, the repo must be named `ferris`.

Push all files in this folder to that repo on the `main` branch.

## 2. Replace placeholders

Globally replace every occurrence of `YOUR_USERNAME` with your actual GitHub username,
and `YOUR_NAME` / `you@example.com` with your real name and email.

Files to update:
- `README.md`
- `index.html`

## 3. Enable GitHub Actions

The workflow in `.github/workflows/update-rust-projects.yml` runs automatically once
you push to `main`. It:
- Fetches all your public Rust repos via the GitHub API
- Sorts them by star count
- Rewrites the project table in `README.md`
- Commits the change back (with `[skip ci]` to avoid loops)

No secrets or tokens needed — it uses the built-in `GITHUB_TOKEN`.

## 4. Host the portfolio site (optional)

To deploy `index.html` as a live website:

1. Go to **Settings → Pages** in your profile repo
2. Set source to **Deploy from a branch → main → / (root)**
3. Your site will be live at `https://YOUR_USERNAME.github.io/YOUR_USERNAME/`

The page auto-fetches your Rust repos from the GitHub API on every visit.

---

## Customisation tips

- **Stack chips**: edit the `#stack` section in `index.html`
- **Code snippet**: update the `about.rs` terminal block in `index.html`
- **Repo cap**: change `slice(0, 8)` in the JS to show more/fewer projects
- **Colours**: tweak `--rust` and `--rust-dim` CSS variables at the top of `index.html`
