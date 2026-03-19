# Lines of Intent
### Every Border Was Someone's Decision

> *Borders are not natural facts. They were drawn by people, in rooms, on specific dates — and they can be redrawn.*

An interactive data visualization tracing how war, empire, and diplomacy redrew the political maps of **Central Europe**, the **Middle East**, and **Post-colonial Africa** across 18 key moments from 1914 to 2003.

---

## Preview

![Static overview — Central Europe 1914–2000](outputs/animation.png)

---

## About

This visualization animates political border changes across three regions of the world:

| Region | Period | Key Events |
|--------|--------|------------|
| Central Europe | 1914–2000 | WWI, Versailles, WWII, German reunification, Yugoslav wars |
| Middle East | 1920–2003 | Sykes-Picot, Israeli independence, Six-Day War, Iraq War |
| Post-colonial Africa | 1938–1993 | Berlin Conference borders, Year of Africa, decolonisation |

Each region is shown across six key historical moments — treaties, wars, independence movements, and collapses of empire. Countries are drawn one by one using a **hand-rendered sketchy aesthetic**, reinforcing the central argument: every line on a political map is a human decision, provisional and erasable.

---

## Interactive Demo

Open `lines-of-intent.html` in any modern browser — no server or internet connection required.

- Switch between the three regions using the region buttons
- Press **play** to animate countries appearing one by one
- Hover over any country to see its name
- Use **skip →** to jump ahead or drag the speed slider

---

## Repository Structure

```
lines-of-intent/
├── lines-of-intent.qmd   # Source document (Quarto)
├── lines-of-intent.html  # Rendered output — open this in a browser
├── outputs/
│   ├── animation.png     # Static overview grid (Central Europe, 300 DPI)
│   ├── animation.html    # Standalone interactive animation
│   └── data_*.js         # GeoJSON boundary data per region
└── README.md
```

---

## How to Reproduce

### Prerequisites

```r
install.packages(c(
  "cshapes", "roughsf", "sf", "ggplot2", "patchwork",
  "MetBrewer", "htmltools", "webshot2", "gifski",
  "dplyr", "jsonlite", "geojsonsf", "ggplotify",
  "htmlwidgets", "png"
))
```

> `webshot2` requires Chromium. If not found, it installs one automatically on first run.

### Render

```r
quarto::quarto_render("lines-of-intent.qmd")
```

Or from the terminal:

```bash
quarto render lines-of-intent.qmd
```

---

## Data & Methods

**Data:** [`cshapes`](https://cran.r-project.org/package=cshapes) R package (Weidmann, Kusa & Gleditsch, 2010) — historically accurate country boundaries for every date from 1886 to present.

**Rendering:** [`roughsf`](https://github.com/schochastics/roughsf) (Schoch, 2022) — converts `sf` geometries to hand-drawn sketchy paths via the `rough.js` engine. Roughness 1.4, bowing 0.8.

**Palette:** [MetBrewer](https://github.com/BlakeRMills/MetBrewer) `Redon` — muted earth tones derived from Odilon Redon's botanical illustrations.

**Concept:** The hand-drawn aesthetic is the argument. Borders rendered in pencil look provisional, erasable, human. The same lines drawn by diplomats in London, Paris, and Berlin still define where people can and cannot go today.

---

## Packages

| Package | Role |
|---------|------|
| `cshapes` | Historical boundary data |
| `roughsf` | Hand-drawn map rendering |
| `sf` | Spatial data handling |
| `ggplot2` + `patchwork` | Static grid output |
| `MetBrewer` | Colour palette (Redon) |
| `webshot2` | Widget → PNG capture |
| `jsonlite` + `geojsonsf` | GeoJSON export |
| `htmlwidgets` | HTML widget serialisation |

---

## Citation

```
Weidmann, N. B., Kusa, D., & Gleditsch, K. S. (2010). The Geography of the International System:
The CShapes Dataset. International Interactions, 36(1), 86–106.
```

---

## License

[MIT](LICENSE)
