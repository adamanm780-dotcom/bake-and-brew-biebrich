# Bake & Brew — Website

Premium Landingpage für **Bake & Brew**, ein authentisch griechisches Café in Wiesbaden-Biebrich
(Stettiner Str. 10). Entwickelt nach einem Referenzdesign im luxuriös-editorialen Premium-Stil,
angelehnt an Awwwards-Ästhetik: türkis-teal + warm cream + matcha-green, Fraunces-Serif für
Headlines, Inter für Body-Text, viel Raum, subtile Mikroanimationen.

**Live:** [bake-brew-wiesbaden.vercel.app](https://bake-brew-wiesbaden.vercel.app/)

---

## Tech-Stack

Bewusst **kein Framework** — reines, produktionsnahes **HTML / CSS / JS**. Grund:
maximale Performance, null Build-Overhead, jeder Handgriff wartbar. Die Seite lädt unter 150 kB,
rendert ohne JS bereits vollständig und ist 100% statisch deploybar.

- `index.html` — semantische Struktur, OpenGraph + JSON-LD `CafeOrCoffeeShop`
- `styles.css` — Design-System (Custom Properties), Fraunces + Inter, ~1500 Zeilen
- Vanilla JS inline — Loader, Sticky Nav, Reveal-on-Scroll, Mobile-Menu, Canvas-Frame-Sequenz

## Struktur der Seite

1. **Loader** (Türkis-Screen mit Logo + Progress-Bar)
2. **Sticky Nav** (transparent → glassy beim Scrollen, echtes Logo)
3. **Hero** — Matcha-Motiv, zentrierte Headline, Scroll-Indicator
4. **Marquee** — endlos laufende Signature-Produkte
5. **Trust Strip** — 4 Qualitäts-Kacheln
6. **Our Bestsellers** — 5 Produktkarten mit CSS-Illustration + Sterne + Preis
7. **Shop by Category** — 4 Kategorie-Cards
8. **„Vom Ofen direkt auf deinen Tisch"** — Editorial Split + 5,0-Google-Badge
9. **Story** — Two-Column mit Stats-Aside (sticky)
10. **Crafted with Care** — 5 nummerierte Handwerks-Prinzipien
11. **Menu** — Scroll-Linked Canvas-Frame-Sequenz + 3 Karten
12. **Atmosphäre** — 4 Feature-Cards
13. **Testimonials** — 3 Google-Review-Zitate + 5,0-Summary
14. **Newsletter** — dunkle Card mit Glass-Form
15. **FAQ** — 6 `<details>`-Items (sticky Heading desktop)
16. **Besuch** — Adresse, Öffnungszeiten, Gut-zu-wissen (dunkle Section)
17. **Final CTA** — „Ein Freddo. Ein Käsekuchen. Ein guter Morgen."
18. **Full Footer** — 4 Columns, Sozial-Icons, Maps-Link, Legal

## Design-System

```
/* Farben */
--teal-500:   #3E9792    /* Primary Teal */
--turq:       #2FB8B0    /* Signature Turquoise */
--turq-bright:#4FD3CA    /* Hover/Accent */
--cream-50:   #FBF6EC    /* Warm Off-White */
--ink-900:    #152524    /* Text */

/* Schrift */
Fraunces 9..144, opsz, 300–700    → Headlines, Zitate
Inter 400–700                      → Body, UI

/* Radius */
10 / 16 / 22 / 28 / 40 px

/* Shadow */
sm → md → lg → ring
```

Alle Werte sind CSS Custom Properties in `:root` — ein Tausch ändert das ganze Produkt.

## Setup / lokal testen

```bash
# Im Ordner bake-brew-website/:
python -m http.server 4173
# oder
npx serve .
```

Dann `http://localhost:4173` öffnen.

## Deploy

Das Projekt ist bereits für **Vercel** konfiguriert (siehe `vercel.json`). Ein `git push`
genügt, bzw.:

```bash
npx vercel --prod
```

Die `vercel.json` aktiviert Long-Term-Caching für `*.webp` / `*.png` und sorgt für saubere
HTTPS-Redirects.

## Assets

Alle aktuell verwendeten Bild-Assets liegen direkt im Ordner:

- `logo.png` — Haupt-Logo (Header + Footer)
- `hero-bg.{webp,jpg}` + `-sm` / `-md` — Hero in 3 Auflösungen + Fallback
- `loading-logo.webp` — Preloader
- `frames/f-01…f-50.webp` — Scroll-Video im Menü (Canvas)

**Optional erweiterbar:** In [ASSETS.md](./ASSETS.md) findest du **fertige Prompts** für
ChatGPT / Midjourney / Replicate, mit denen du die SVG-Platzhalter in den Product-Cards und
im Editorial Split durch echte Foto-Assets ersetzen kannst. Jeder Prompt enthält Style-Guide,
Seitenverhältnis, Dateinamen und Integrations-Snippet.

## SEO &amp; Performance

- **JSON-LD** `CafeOrCoffeeShop` mit Öffnungszeiten, Koordinaten, aggregateRating 5,0
- **Open Graph** + **Twitter Card** für Sharing
- `hero-bg` per `<link rel="preload">` mit responsive `srcset`
- Font-Preconnect zu Google Fonts
- Kein JS-Framework → First-Contentful-Paint bleibt niedrig
- `robots.txt` + `sitemap.xml` vorhanden

## Anpassen

**Produkt hinzufügen:** In `index.html` unter `#bestsellers` einen neuen `<article class="product-card" data-accent="…">`
Block einfügen. Für das `data-accent`-Attribut gibt es 5 Farbvarianten in `styles.css` — einfach
eine weitere anlegen.

**Öffnungszeiten ändern:** Gesucht nach `05:30` — die Zeiten sind im Visit-Block, im Footer und
im JSON-LD jeweils einmal definiert.

**Testimonials austauschen:** Section `#reviews` — die `<blockquote>` Inhalte sind echte
Zusammenfassungen aus `Bake.md` (Google-Reviews). Bei neuen Reviews einfach ersetzen.

**Logo ändern:** Die Datei `logo.png` austauschen — wird 1:1 im Header (`.brand__mark--img`)
und Footer (`.foot__logo`) verwendet.

## Credits

- Fonts: [Fraunces](https://fonts.google.com/specimen/Fraunces) (OFL),
  [Inter](https://fonts.google.com/specimen/Inter) (OFL)
- Icons: maßgeschneidert als Inline-SVG
- Hero-Motiv: aus `matcha.png` (Projekt-Asset)
- Content: Bake &amp; Brew, Stettiner Str. 10, 65203 Wiesbaden — basierend auf `Bake.md` +
  Google-Maps-Reviews
