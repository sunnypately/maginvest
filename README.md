# Strategic Co-Investment Tracker

A single-file dashboard for tracking strategic co-investment positions, built with the institutional dark-terminal aesthetic (Libre Baskerville + JetBrains Mono, gold accents on near-black).

## Live site

Once deployed via GitHub Pages, the dashboard is available at:

```
https://<your-github-username>.github.io/<repo-name>/
```

## Local preview

No build step. Just open the file directly:

```bash
open index.html
```

Or serve it locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a new GitHub repository and upload `index.html` and `README.md`.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
4. Select the `main` branch and `/ (root)` folder, then **Save**.
5. Wait ~1 minute, then visit the URL shown in the Pages settings.

## Structure

```
.
├── index.html    # Self-contained dashboard (HTML + CSS + JS)
└── README.md
```

All styles and scripts are inlined — no external dependencies beyond Google Fonts (Libre Baskerville, JetBrains Mono).
