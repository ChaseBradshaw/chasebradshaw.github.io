# portfolio

Static portfolio website with a retro/brutalist aesthetic, built for **GitHub Pages**. Uses Tailwind CDN and vanilla JS.

## Structure

```
portfolio/
├── index.html              # Homepage (hero, featured projects, skills, contact)
├── work.html               # Work listing (career / professional projects)
├── projects.html           # Projects listing (side projects)
├── work/
│   └── overseer-matrix.html   # Example work detail
├── projects/
│   └── sustainable-goods.html # Example project detail
├── css/
│   └── main.css            # Shared design system & utilities
├── js/
│   └── main.js             # Shared scripts
├── assets/
│   └── images/             # Images and icons
├── design_mock/            # Reference mocks (Page_1–3)
└── .cursor/
    └── rules/              # Cursor AI rules
```

**Flow:** Home → Work or Projects (listing) → detail page. Top-level nav on every page: **Home** | **Work** | **Projects**.

## Local preview

Open `index.html` in a browser, or serve the root folder (e.g. `npx serve .` or VS Code Live Server). All links use relative paths so navigation works without a server.

## Deploy to GitHub Pages

1. Push this repo to GitHub.
2. **Settings → Pages** → Source: deploy from branch `main` (or your default), folder **/ (root)**.
3. Site will be at `https://<username>.github.io/portfolio/`.
