STEM interactive learning website.

# Lizard-Spock STEM — Handoff & Progress

Interactive STEM learning site for ages 10+. Friendly-but-factual tone.
**Chosen direction: 1a "Graph-paper field lab"** (warm paper `#faf6ef`, graph-grid bg, ink `#2b2620`, orange accent `#e8590c`, hard 2px ink borders + offset shadows) blended with 1c's friendly "Eight worlds to explore" topic list.

## Design system (apply everywhere)
- Fonts: Archivo (display, 800/900, tight tracking) · Space Grotesk (body) · IBM Plex Mono (annotations, labels, buttons)
- Colors: paper `#faf6ef`, ink `#2b2620`, muted `#6b6156`, border `#d8d0c4`, accent `#e8590c`, white cards `#fff`
- Motifs: `// FIG. 0N — LABEL` mono section headers, 2px ink borders, `4px 4px 0` ink offset shadows on primary buttons, graph-paper background via repeating-linear-gradient (24px)
- Copy tone: friendly but factual, ages 10+. No emoji.

## Site structure
- Everything deployable lives in `public/`. Entry: `public/index.html`.
- Pages authored as Design Components (`.dc.html`), copied to plain `.html` names for deployment (support.js must be alongside).
- `Homepage Options.dc.html` (project root) = the 3 original design options; keep for reference.

## Topic plan (8 worlds)
1. **Chemistry — LIVE**: interactive periodic table (first module)
2. Physics — forces/motion/energy sims (coming soon)
3. Biology — cells → ecosystems (coming soon)
4. Math — graphing, geometry, probability (coming soon)
5. Astronomy — solar system to scale (coming soon)
6. Earth Science — plate tectonics, weather, rocks (coming soon)
7. Engineering — bridges, circuits, design challenges (coming soon)
8. Coding — logic puzzles, first programs (coming soon)

## Periodic table feature list (agreed with user)
- [ ] Full 118-element grid (18 cols, lanthanide/actinide rows), color-coded by category
- [ ] Click element → detail panel: properties, uses, fun fact
- [ ] Color-mode toggle: category / state-at-temperature
- [ ] Temperature slider (0–6000 K) driving solid/liquid/gas coloring
- [ ] Electron shell diagram (Bohr-style) in detail panel
- [ ] Quiz: "find the element" game with score/streak

## Progress log
- ✅ Asked design questions; user picked: science-lab feel, warm & energetic, all 8 topics, full periodic-table feature set, coming-soon cards for other topics, mix tone, brand "Lizard-Spock STEM"
- ✅ 3 homepage options built (`Homepage Options.dc.html`); user chose 1a + 1c's friendly topic list
- ✅ `public/elements.js` — full 118-element dataset (mass, category, group/period, melt/boil K, shells, fun fact) + CATEGORIES/STATE_COLORS palettes + `stateAt()` + `gridPos()` helpers
- ✅ `public/periodic-table.dc.html` — full table: 118 tiles, family/state color modes, temp slider (0–6000 K), detail panel (props, Bohr shell diagram SVG, fun fact), quiz mode (score/streak/skip)
- ✅ `public/index.dc.html` — homepage (1a style, hero + teaser grid + "Eight worlds" list, Chemistry LIVE)
- ✅ Copied DCs → `public/index.html`, `public/periodic-table.html`; `public/support.js` present (deploy the `public/` folder as-is)
- ✅ Verifier pass 1: fixed grid overflow (minmax(0,1fr) + overflow-x wrapper) and removed overlapping f-block pointer cells
- ✅ Search box (name/symbol/number, dims non-matches), field-log "N of 118 inspected" (localStorage `lizard-spock-stem.inspected`), quiz levels LV.1 name / LV.2 masked-fact clue
- ✅ `public/atom-3d.js` — <atom-3d> canvas web component: 3D Bohr atom, drag-to-rotate, auto-spin, live orbiting electrons; used in table detail panel + article
- ✅ `public/electron-shells.dc.html` — Field Guide 01 article: shells/energy levels (hotel-floor analogy, 2n² capacities, photon jumps, valence, Bohr-model caveat) + interactive 3D atom playground w/ 6 element presets; linked from detail panel ("READ: HOW ELECTRON SHELLS WORK")
- ⬜ Verify electron-shells + updated periodic-table

## Known bugs / future updates (to fix)
- `public/electron-shells.dc.html` (+ deployed `.html`): add a visual at the top of the article — a labelled intro atom diagram (nucleus + shells) beside/under the hero — so the "How electrons live in energy levels" intro makes sense for readers who didn't arrive from the periodic table. Could reuse `<atom-3d>` with a caption/labels.
- `public/atom-3d.js`: nucleus is drawn as a single orange dot with the element symbol at centre. Should instead render a proton/neutron cluster (packed small spheres, two colors, count from atomic number/mass) at the centre; move the symbol label elsewhere (e.g. below the canvas). Affects periodic-table detail panel + electron-shells article.
- `public/electron-shells.dc.html` (+ deployed `.html`): add an animation showing an electron changing energy levels — absorbs energy → jumps to a higher shell, then falls back down → emits a photon (a little light-wave/flash carrying the extra energy). Fits section 04 (photon jumps). Build as a canvas/JS component (like `atom-3d.js`) or `React.createElement` animated element per DC animation rules; loop or play-on-click.
- New page: `public/states-of-matter.dc.html` — Field Guide 02: the four fundamental states of matter (solid, liquid, gas, plasma). Same article style as electron-shells (mono `// 0N` headers, Archivo/Space Grotesk/Plex Mono, warm paper). Explain particle arrangement/energy per state, transitions (melt/boil/ionize). Good candidates: animated particle-box demo per state; link from periodic table's state color-mode / temperature slider ("READ: STATES OF MATTER").

## Next ideas (not committed)
- Element "collection" progress (localStorage) — mark elements you've inspected
- Quiz difficulty levels (name→click, clue→click, symbol→name)
- Second module candidate: solar system to scale (Astronomy)

