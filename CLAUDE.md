# Pixel's World — site_proj

Landing page pentru Pixel's World, brand care vinde albume foto premium pentru bebeluși pe eMAG și direct.

## Produse

| Cod   | Nume              | Culoare  | Preț   | Pagini | Foto |
|-------|-------------------|----------|--------|--------|------|
| PXL-2 | Povestea Mea      | Roz      | 90 Lei | 42     | 50   |
| PXL-1 | Povestea Mea      | Albastru | 90 Lei | 42     | 50   |

Format: 210×210 mm pătrat, copertă plus (moale, catifelată), hârtie extra-presată, legătură cusută.

## Stack

- HTML5 / CSS3 / Vanilla JS (ES6+) — fără framework sau build tool
- Limbă: română

## Structura fișierelor

```
site_proj/
├── index.html          # Landing page principală
├── pages/
│   ├── about.html      # Despre noi
│   └── contact.html    # Formular comandă/contact
├── css/
│   ├── reset.css
│   └── style.css       # Design system complet (variabile, BEM)
├── js/
│   └── main.js
└── assets/
    ├── images/         # Fotografii produse, hero, etc.
    ├── fonts/
    └── icons/
```

## Design

- Paletă: roz (#db2777), albastru (#2563eb), auriu (#f59e0b), fundal alb cald (#fdf8ff)
- CSS custom properties în `:root`
- BEM pentru clase
- Fonturi: system-ui

## Convenții

- JS: `const`/`let`, fără `var`
- CSS: BEM — `.block__element--modifier`
- Imaginile produselor merg în `assets/images/`
