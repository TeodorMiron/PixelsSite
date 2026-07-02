# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

# Pixel's World — site_proj

Landing page pentru Pixel's World, brand care vinde albume foto premium pentru bebeluși pe eMAG și direct.

## Comenzi dezvoltare

```bash
npm run dev   # pornește browser-sync cu live reload pe http://localhost:3000
```

Nu există build step, linter sau test suite — fișierele sunt servite direct din sursă.

## Produse

| Cod   | Nume         | Culoare  | Preț   | Pagini | Foto |
|-------|--------------|----------|--------|--------|------|
| PXL-2 | Povestea Mea | Roz      | 100 Lei| 42     | 50   |
| PXL-1 | Povestea Mea | Albastru | 100 Lei| 42     | 50   |

Format: 210×210 mm pătrat, copertă plus (moale, catifelată), hârtie extra-presată, legătură cusută.

## Arhitectură

Site static (GitHub Pages, domeniul `www.pixelsworld.ro` via `CNAME`): `index.html`, `404.html`, `pages/about.html`, `pages/contact.html` și blogul în `pages/blog/` (index + 3 articole). Toate partajează `css/reset.css` + `css/style.css` și `js/main.js`.

**`js/main.js`** conține toată logica interactivă: hamburger menu, smooth scroll, gallery tabs (roz/albastru), lightbox cu navigare cu tastatura (←/→/Esc).

**`css/style.css`** este design system-ul complet: variabile CSS în `:root`, urmate de componente BEM (`nav`, `hero`, `product-card`, `gallery`, `lightbox`, `why-card`, `review-card`, `faq`, `cta`, `footer`).

**Comenzile** se plasează pe eMAG (butoanele „Comandă pe eMAG"); pagina de contact are doar email + link-uri eMAG, fără formular.

**Paths:** `index.html`/`404.html` folosesc path-uri directe; `pages/` folosește `../`, `pages/blog/` folosește `../../` (404.html folosește path-uri absolute `/...` pentru că se servește de la orice adâncime).

Imaginile produselor au nume SEO în `assets/images/album_roz/` (`album-foto-bebelusi-roz-1..9.jpg` + `-video.mp4`) și `assets/images/album_albastru/` (`album-foto-bebelusi-albastru-1..13.jpg` + `-video.mp4`); toate au 1600×1066 px, cu excepția `roz-9` (1066×1066). Folderele-sursă (`DateProduse/`, `pixel albume/`, `poze si video album */`, fișierele `WhatsApp*`) sunt în `.gitignore` — există doar local, nu se publică.

## SEO

- `sitemap.xml` + `robots.txt` în root; fiecare pagină are meta description unică, `canonical` și Open Graph
- JSON-LD pe `index.html`: Organization, WebSite, 2× Product (preț/rating), FAQPage, 2× VideoObject; pe blog: BlogPosting + BreadcrumbList
- Google Analytics 4 (`G-95DQB4P9X3`) în `<head>` pe toate paginile
- La schimbarea prețului: actualizează și `"price"` din JSON-LD (index.html), nu doar textul vizibil

## Design system

- Paletă: `--pink-dark: #db2777`, `--blue-dark: #2563eb`, `--gold: #f59e0b`, `--off-white: #fdf8ff`
- Variabilele complete sunt în `css/style.css:1-15`
- BEM strict: `.block__element--modifier`; stare activă marcată cu `.is-active` / `.is-open`
- Fonturi: `system-ui` (fără import extern)

## Convenții

- JS: `'use strict'`, `const`/`let`, fără `var`
- Toate textele sunt în română
- Noi pagini în `pages/` folosesc path-uri relative cu `../`
- CSS page-specific se adaugă inline în `<style>` în `<head>`, nu în fișiere noi
