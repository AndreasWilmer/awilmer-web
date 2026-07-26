# Projekt: awilmer-web (GitHub Pages)

Persönliche Website + Tutorials-Doku. Repo-Owner ist der GitHub-User
`AndreasWilmer` (nicht "awilmer" — das ist ein anderer, leerer Account,
darauf achten bei URLs und Links).

## Struktur

- `landing/` — statische Landingpage (Hero, Bio, Footer), reines HTML/CSS,
  kein Build-Step
- `docs/` — MkDocs-Quellen (Markdown) für die Tutorials-Sektion
- `mkdocs.yml` — MkDocs-Material-Konfiguration
- `.github/workflows/deploy.yml` — einziger Deploy-Mechanismus

## Deployment — WICHTIG, nicht zurückbauen

- **Niemals** `mkdocs gh-deploy` direkt oder im Workflow verwenden — das
  überschreibt den kompletten `gh-pages`-Branch nur mit dem MkDocs-Build
  und löscht dabei die Landingpage.
- Korrekter Ablauf im Workflow:
  1. `mkdocs build --site-dir _deploy/tutorials` (MkDocs baut in Unterordner)
  2. `cp -r landing/* _deploy/` (Landingpage daneben kopieren)
  3. `peaceiris/actions-gh-pages@v4` deployed den kompletten `_deploy/`-Ordner
     nach `gh-pages`
- Live-URLs:
  - `https://andreaswilmer.github.io/awilmer-web/` → Landingpage
  - `https://andreaswilmer.github.io/awilmer-web/tutorials/` → MkDocs-Doku
- GitHub Pages Settings: Source = "Deploy from a branch", Branch = `gh-pages`,
  Ordner `/ (root)`

## Landingpage-Konventionen

- Fonts: Rubik (Headings/Nav), Inter (Body) — via Google Fonts CDN, nicht
  selbst hosten
- Logo: `landing/images/logo.png` (echtes Originalbild), dargestellt in
  weißem Hexagon-Badge via CSS `clip-path` (Klasse `.logo-badge` in
  `css/style.css`) — kein SVG-Nachbau verwenden
- Kein Kontaktformular — bewusst entfernt. Kontaktseite verlinkt nur
  `mailto:`
- Nav-Textgröße 1.2rem, Icons 20px (bewusst vergrößert)
- Header/Footer sind in jeder HTML-Datei dupliziert (kein Templating).
  Änderungen an Nav oder Footer müssen synchron in allen 5 Dateien gemacht
  werden: `index.html`, `recipes.html`, `contact.html`, `impressum.html`,
  `privacy.html`

## Offene Punkte

- Amber-Akzentfarbe (`--color-accent: #d98f3c`) ist geschätzt, nicht der
  echte Original-Hex-Wert
- `docs/index.md` etc. enthalten noch MkDocs-Platzhaltertext, kein echter
  Tutorial-Inhalt
- Recipes-, Contact-, Impressum-Seiten sind Platzhalter-Stubs
