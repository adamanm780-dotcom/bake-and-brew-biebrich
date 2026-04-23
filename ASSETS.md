# Bake & Brew — Asset Guide

Diese Datei listet alle Bild-/Video-Assets auf, die die Website aktuell als **CSS/SVG-Platzhalter** rendert.
Jeder Eintrag enthält einen **fertigen Prompt** für ChatGPT (DALL·E 3 / GPT-4o Image),
**Midjourney** oder **Replicate**, sowie den Ziel-Dateinamen und die Stelle, an der das Bild
eingebunden wird.

> Stil-Leitplanke für **alle** generierten Bilder:
> *Editorial product photography, soft natural light, matte finish, muted palette — türkis-teal,
> warm cream, matcha-green, gentle caramel highlights. Shallow depth of field. Magazine-grade.
> No text on image, no logo overlays, no people mid-pose — quiet, elevated, premium.*

---

## Aktuell verwendete Dateien

| Datei | Zweck | Status |
| --- | --- | --- |
| `logo.png` | Logo in Header &amp; Footer | ✅ eingebaut (aus `bakem.png`) |
| `hero-bg.webp`, `hero-bg-md.webp`, `hero-bg-sm.webp`, `hero-bg.jpg` | Hero-Background | ✅ eingebaut (aus `matcha.png`) |
| `loading-logo.webp` | Preloader | ✅ vorhanden |
| `frames/f-01.webp` – `frames/f-50.webp` | Scroll-Video im Menü | ✅ vorhanden |

## Optional generierbare Upgrades

Die folgenden Elemente sind aktuell als elegante **CSS/SVG-Illustrationen** gestaltet. Wenn
du echte Foto-Assets ergänzen möchtest, nutze die Prompts unten.

---

### 1. Product Cards (5 Stück)

**Einsatz:** Section `#bestsellers` — die `<div class="product-card__media">` Blöcke.
**Empfohlenes Format:** 1200×900 px, WebP oder JPG, Dateinamen siehe Spalte.

| Produkt | Dateiname | Prompt |
| --- | --- | --- |
| Iced Matcha Latte | `product-matcha.webp` | *Tall glass of iced matcha latte, translucent layered green, ice cubes, bamboo straw, soft teal paper backdrop, top-down-slightly-angled product photo, natural window light from the left, sharp on the glass, 45mm lens, matte finish, subtle water droplets, shallow depth of field, no text, no logo.* |
| Freddo Espresso | `product-freddo.webp` | *Tall thin glass of Greek freddo espresso, thick creamy crema layer on top, ice cubes melting, condensation droplets, warm caramel tones, teal-cream editorial background, 45mm product shot, soft window light, no text.* |
| Käsekuchen | `product-cake.webp` | *A thin slice of homemade Greek cheesecake on a small plate, golden crust, creamy filling, drizzle of honey, fresh pistachios, rustic ceramic plate, warm linen tablecloth, overhead-ish angle, soft natural light, muted cream palette with a hint of matcha green in the background.* |
| Spanakopita | `product-spanakopita.webp` | *Freshly baked golden spanakopita, flaky phyllo pastry, visible spinach-feta filling, served on a small ceramic plate, rustic wooden board, soft warm light, very appetizing crumbs around, editorial shot, no text.* |
| Freddo Cappuccino | `product-freddo-cap.webp` | *Tall glass of Greek freddo cappuccino, smooth velvety cold foam on top, rich espresso below, ice, condensation, teal backdrop, product shot, soft cinema light, 45mm lens, no logo, no text.* |

**Integration:** Ersetze den SVG `.product-card__art` Block innerhalb der jeweiligen
`<div class="product-card__media">` durch:

```html
<img class="product-card__art" src="product-matcha.webp"
     alt="Iced Matcha Latte in hohem Glas" width="800" height="600"
     loading="lazy" decoding="async" />
```

---

### 2. Editorial Split — „From our oven"

**Einsatz:** Section `#oven`, innerhalb `.split__collage`.

| Slot | Dateiname | Prompt |
| --- | --- | --- |
| Hauptbild (links, hochformat) | `oven-bread.webp` | *Golden crusty sourdough and Greek tiropita loaves cooling on a wooden bakery counter, soft early-morning light from the side, flour dust in the air, warm cream and caramel palette, shot on a medium format camera, editorial bakery photography, shallow depth of field, no text, no people faces.* |
| Nebenbild (rechts, hochformat) | `oven-drink.webp` | *Barista pouring steamed milk into a matcha latte in a tall glass, hands in frame but face not visible, bright airy café interior in the background, teal tiles, morning light, editorial lifestyle shot.* |

**Integration:** Ersetze `.collage-card__art` SVGs durch `<img>`-Tags mit diesen Dateien.

---

### 3. Hintergründe & Atmosphäre (optional)

| Slot | Dateiname | Prompt |
| --- | --- | --- |
| Atmosphäre-Abschnitt Detail | `cafe-interior.webp` | *Bright modern-minimalist Greek café interior in Wiesbaden-Biebrich, white plaster walls, light oak counter, a few bentwood chairs, morning sun, no people, calm atmosphere, warm cream + muted teal accents, architectural magazine photography.* |
| Hintergrund-Textur (subtil) | `texture-linen.webp` | *Soft cream linen texture, barely visible threads, neutral background, tileable, matte, very high resolution.* |

---

### 4. Videos (Replicate) — optional

Sinnvoll nur, wenn du einen zusätzlichen Premium-Effekt möchtest. Die Website funktioniert
auch ohne Video-Loops stark. Modelle: `minimax/video-01`, `luma/dream-machine`, `wan-video/wan-2.2-i2v-a14b`.

| Loop | Dateiname | Prompt |
| --- | --- | --- |
| Matcha-Pour Loop | `loop-matcha.mp4` | *Slow cinematic loop: matcha being whisked in a chawan with bamboo whisk, rich green foam forming, natural window light, top-down angle, 8-second seamless loop, 24fps, no text.* |
| Freddo-Pour Loop | `loop-freddo.mp4` | *Espresso being poured over ice in a tall glass, slow motion, rich crema forming, 8-second seamless loop, warm light, minimalist backdrop, product shot.* |
| Bread-Steam Loop | `loop-bread.mp4` | *Fresh sourdough loaf steaming on a wooden board, soft light, slow camera push-in, 6-second seamless loop, bakery atmosphere.* |

**Integration (Beispiel — Hero):**

```html
<video class="hero__video" autoplay muted loop playsinline poster="hero-bg.webp">
  <source src="loop-matcha.mp4" type="video/mp4" />
</video>
```

---

## Konsistenz-Checkliste

Bevor du generierte Bilder einbaust, kurz prüfen:

- [ ] **Farbwelt:** Türkis-teal + warm cream + matcha-green dominieren
- [ ] **Licht:** weich, natürlich, leicht diffus — kein hartes Studiolicht
- [ ] **Komposition:** ruhig, editorial, viel Raum um das Motiv
- [ ] **Details:** kleine Imperfektionen (Brösel, Tropfen, Krusten) erlaubt — wirkt handwerklich
- [ ] **Keine Texte, Logos, Wasserzeichen im Bild**
- [ ] **Kein Stock-Look** (keine übertriebene Sättigung, keine Linsen-Flares, keine „foodporn"-Ästhetik)

## Workflow-Tipp

1. Generiere in ChatGPT/Midjourney jeweils **4 Varianten pro Prompt**
2. Wähle die beste, exportiere als PNG
3. Konvertiere zu WebP: `cwebp -q 82 input.png -o output.webp`
4. Lege die Datei direkt neben `index.html` ab
5. Tausche die SVG-Platzhalter gegen `<img>`-Tags aus (siehe Integration oben)
