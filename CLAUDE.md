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

Site static cu trei pagini HTML; toate partajează `css/reset.css` + `css/style.css` și `js/main.js`.

**`js/main.js`** conține toată logica interactivă: hamburger menu, smooth scroll, gallery tabs (roz/albastru), lightbox cu navigare cu tastatura (←/→/Esc).

**`css/style.css`** este design system-ul complet: variabile CSS în `:root`, urmate de componente BEM (`nav`, `hero`, `product-card`, `gallery`, `lightbox`, `why-card`, `review-card`, `cta`, `footer`).

**`pages/contact.html`** include CSS page-specific inline (`<style>`) și un handler `submit` inline care afișează `alert()` — nu există backend real pentru formular.

**`pages/about.html`** și **`pages/contact.html`** referențiază assets cu path relativ (`../css/`, `../js/`); `index.html` folosește path-uri directe (`css/`, `js/`).

Imaginile produselor sunt organizate în `assets/images/album_roz/` (roz_1.jpg … roz_9.jpg + roz_video.mp4) și `assets/images/album_albastru/` (albastru_1.jpg … albastru_13.jpg + albastru_video.mp4).

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
