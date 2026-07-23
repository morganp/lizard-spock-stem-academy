# Project instructions — Lizard-Spock STEM Academy

Interactive STEM learning site, ages 10 → A-level / Advanced Higher. House style: warm paper `#faf6ef`, ink `#2b2620`, orange accent `#e8590c`, graph-paper background, 2px ink borders, `4px 4px 0` offset shadows; fonts Archivo (display) · Space Grotesk (body) · IBM Plex Mono (labels). Every page authored as `Name.dc.html`, then copied to a deploy `.html` of the same name. See HANDOFF.md for the full progress log and structure.

## 1. Figure / table / graph labelling standard (apply to EVERY page)
Consistency here is a hard requirement — the site is meant to feel like a scientific journal.
- **Numbered caption on every figure, table and graph.** Use a mono eyebrow *inside or directly above the framed element*, not just the section header:
  - Figures/diagrams/interactives: `// FIG. 0N — TITLE` (e.g. `// FIG. 02 — WHERE A TREE'S DRY MASS COMES FROM`).
  - Tables: `// TABLE 0N — TITLE`.
  - Graphs/charts: `// GRAPH 0N — TITLE`.
- **Number sequentially within a page**, starting at 01, in reading order. The page's opening hero eyebrow may stay `// FIG. 01 — …` only if it captions an actual figure; otherwise start figure numbering at the first real figure.
- **Every non-obvious element gets a legend or inline label.** Identify every colour, shape and icon (what is orange, what is grey, which dot is which particle/ion/atom). A colour used with meaning MUST appear in a legend.
- **Graphs:** always label both axes **with units** (not just tick numbers); include the legend if more than one series.
- **Legible at true render size** — never shrink label text below the minimums in §2 to cram more in; simplify the figure instead.
- **One level of abstraction per figure** — don't inject atomic substructure into a molecular/mixture-level diagram; make a dedicated figure and cross-link.
- When editing an existing page, renumber figures if you insert one in the middle so the sequence stays contiguous.

## 2. Minimum sizes (readability & consistency)
We have a site-wide tendency to draw things too small — especially arrows. Enforce these floors:
- **Arrows in any diagram/canvas:** stroke width **≥ 2px** (≥ 3px when it's the active/highlighted arrow); **arrowhead ≥ 10px** long (≥ 14px when active/emphasised). No hairline arrows. This applies to SVG paths, canvas strokes, and CSS.
- **Diagram/figure label text ≥ 9px** (mono). Body copy: ≥ 13px on screen. Slide text ≥ 24px. Print ≥ 12pt.
- **Interactive hit targets ≥ 44×44px** (buttons, clickable nodes, legend chips, sim controls).
- **Legend swatches ≥ 11px.**
- Canvas components: size the drawing so these minimums hold at the component's actual mounted width — scale the whole scene up rather than shipping tiny marks.

## 3. References & citations standard
Every content/topic page (not maps) ends with a **`// REFERENCES & FURTHER READING`** block before the "next" nav:
- Cite **2–4 sources**. Prefer **Wikipedia** (stable article titles — e.g. `en.wikipedia.org/wiki/State_of_matter` — low staleness risk, free) and **BBC Bitesize** (`bbc.co.uk/bitesize`, reputable, free) for the concepts on the page.
- Links open in a new tab: `target="_blank" rel="noopener"`, styled in blue (`#2a6fb0`) with a `↗` affordance.
- Avoid deep-linking fragile URLs that rot; prefer canonical article/hub URLs. Don't cite sources you haven't sanity-checked for credibility.
- End with a one-line note: "Cross-check against your own exam board's specification (AQA, Edexcel, OCR, SQA)."

## 4. Next-topic linking rule
The bottom nav of a topic page must move the learner **forward**, never sideways into the same topic:
- Offer the **next topic at the same level** (labelled `NEXT AT THIS LEVEL`) and/or a **level-up** link (labelled e.g. `Level up: … (L2–L3)`), following the dependency graph on that subject's map.
- Never make the primary "next" button link back to the page you're on or to a topic already covered above it.
- Keep a secondary link back to the subject map, but it is not the primary call to action.

## Scientific accuracy
- Keep labelling scientifically accurate; simplify rather than mislead.
- Flag exam-board divergence inline where GCSE / National 5 / A-level / Advanced Higher differ, rather than forking the page.
