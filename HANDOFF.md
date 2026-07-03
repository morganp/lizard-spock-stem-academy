# Lizard-Spock STEM Academy — Handoff & Progress

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

## Curriculum (see `uploads/curriculum-plan.md` — canonical)
- Levels L1 EXPLORER (10–11) → L5 EXPERT (17–18, A-level Yr2 / Adv Higher); every topic/article gets a level badge; site filterable by level/track (GCSE vs Nat5 vs A-level vs Adv Higher, flag syllabus divergence inline).
- Full leveled topic lists for Chemistry, Physics, Biology, Earth Science, Astronomy.
- Interaction-pattern catalog (DIAGRAM, MODEL3D, SIM, BUILDER, ANIM, COMPARE, GRAPH, QUIZ, LAB, CALC, TIMELINE, MAP, SORT, SANDBOX, ARTICLE) — build each engine once, reuse across subjects.
- Build order: 1) DIAGRAM engine 2) SIM engine 3) BUILDER 4) generalize QUIZ from periodic-table; rest as needed.
- Next module suggestion: Physics forces/motion (L1–L3). Math/Engineering/Coding lists still to be written.

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
- ✅ Asked design questions; user picked: science-lab feel, warm & energetic, all 8 topics, full periodic-table feature set, coming-soon cards for other topics, mix tone, brand "Lizard-Spock STEM Academy"
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

- ✅ Nucleus fix: `atom-3d.js` now draws a packed proton(orange)/neutron(grey) 3D cluster (capped ~44 nucleons); symbol moved to corner label
- ✅ `electron-shells.dc.html`: labelled intro carbon-atom diagram (FIG. 01 legend) + `public/photon-jump.js` looping photon-emission animation (FIG. 02, section 04)
- ✅ `public/particle-box.js` — <particle-box> canvas sim (solid/liquid/gas/plasma behaviors)
- ✅ `public/states-of-matter.dc.html` — Field Guide 02 (L1–L2 badge): 4 states + interactive particle box + transitions grid; linked from periodic-table detail panel + cross-linked with FG01
- ⬜ Verify states-of-matter + updated periodic-table
- ✅ Level badges: homepage "LIVE NOW · L1–L3" + levels legend line, FG01 header "LEVEL L2–L3", FG02 "L1–L2", periodic-table READ links carry levels
- ✅ MODULE 2 — Physics forces/motion (L1–L3): `public/force-sim.js` <force-sim> crate-lab canvas sim (push/mass/μ sliders, free-body arrows, static vs kinetic friction, live v–t graph, treadmill ground) + `public/forces-motion.dc.html` page (challenges cards, L1 pushes/pulls → L2 balanced/unbalanced → L3 Newton's laws + graph reading); homepage Physics now LIVE → forces-motion.html
- ✅ Chemistry world map (`public/chemistry.dc.html`): nonlinear dependency graph, all ~38 curriculum topics, L1–L5 bands, live nodes clickable, live-list cards below. Homepage Chemistry card now points here (was periodic-table.html directly).
- ✅ Chemistry L1–L2 sweep (5 new pages, all wired into the graph + liveList):
  - `public/acids-bases.dc.html` + `public/ph-sim.js` — pH slider SIM, indicator colour, neutralisation
  - `public/matter-classify.dc.html` + `public/particle-diagram.js` — element/compound/mixture particle diagrams + click-to-sort game + separating techniques cards
  - `public/word-equations.dc.html` — reaction equation BUILDER (5 reactions: combustion, rusting, neutralisation, displacement, oxide formation)
  - `public/reactivity-series.dc.html` — drag-rank (▲▼) 7-metal reactivity series game with displacement explainer
  - `public/materials-resources.dc.html` — material↔property click-match game + mined/grown/made resource cards
- ✅ Chem L3: `public/bonding.dc.html` + `public/bond-diagram.js` — ionic/covalent/metallic tabbed live diagrams (electron transfer arrow, shared pair, electron sea)
- ✅ Graph layout bug fixed: nodes now flow-wrap per level based on estimated label width (was naive even-spacing causing overlaps on L2/L3 rows) — verified 0 overlaps across all 38+ nodes via DOM measurement
- ✅ Name change: "Lizard-Spock STEM" → "Lizard-Spock STEM Academy" across all live pages + HANDOFF
- ⬜ Verify all new pages load cleanly + chemistry graph layout holds with 8 live nodes
- ✅ Chem L3: `public/bonding.dc.html` + `public/bond-diagram.js` — ionic/covalent/metallic tabbed live diagrams (electron transfer arrow, shared pair, electron sea)
- ✅ Chem L3: `public/rates-of-reaction.dc.html` + `public/rate-sim.js` — collision-theory flask sim (concentration/temp/surface-area sliders, live gas-collection + rate sparkline)
- ✅ Chem L3: `public/energetics.dc.html` + `public/energy-profile.js` — exo/endothermic energy-profile diagram (Eₐ + ΔH labelled), tabbed
- ✅ Chem L3: `public/electrolysis.dc.html` + `public/electrolysis-sim.js` — live cation/anion migration + discharge animation between labelled electrodes
- ✅ Progress tracking system (local-only, Firebase-ready): `public/progress-store.js` (localStorage, visited/completed API, TOPICS registry), wired into all 13 live pages' componentDidMount + completion conditions; `public/chemistry.dc.html` map shows green ✓ checkmarks; new `public/progress.dc.html` profile page (stats, % bar, per-topic status, disabled "Sign in with Google" stub)
- ✅ `firebase.md` — step-by-step for user to create Firebase project, enable Google auth + Firestore, set security rules, and hand back the web config so real cross-device sign-in can be wired in
- ⬜ Verify all 4 new L3 pages load cleanly + progress tracking end-to-end (spot-checked manually, looks correct)
- ✅ Chem L3 sweep complete (5 more pages): `periodic-trends.dc.html` (real-data bar charts: radius/reactivity/melting point), `quantitative-chem.dc.html` (mass↔moles calculator, 6 substances), `organic-intro.dc.html` + `chain-diagram.js` (alkane/alkene chain builder), `chemical-analysis.dc.html` (flame-test match game + gas test reference), `atmosphere-climate.dc.html` + `atmos-pie.js` (composition donut + greenhouse effect toggle)
- ✅ All wired into chemistry map, progress-store TOPICS, and liveList — **L1–L3 chemistry curriculum is now 100% covered**, 18 live topics total (17 chem + 1 physics)
- ✅ Chem L3: `public/salts.dc.html` + `public/titration-curve.js` — salt-building (metal/base/carbonate partners) + live titration pH-curve. **This was the last L3 topic — L1–L3 chemistry curriculum is now literally 100% complete: 19 live chem topics + 1 physics module.**
- ✅ `public/particle-diagram.js` reworked twice: (1) real substance examples (Au/O₂ element, NaCl compound, air's N₂/O₂/Ar mixture) with in-canvas legends per CLAUDE.md figure standard; (2) bonds redrawn as touching/overlapping circles (space-filling style, matches BBC Bitesize/knowledge-organiser convention) instead of stick lines; Element diagram now shows two clearly divided, individually-legended examples (metal/unbonded vs. diatomic gas/bonded) so they don't read as a mixture. `matter-classify.dc.html`: added missing `techniques` data (verifier caught cards rendering empty), added `// FIG. 0N` captions above all three particle diagrams.
- ⬜ Remaining for full curriculum: all of L4–L5 chemistry (stoichiometry, equilibria, redox, further organic, nuclear, thermodynamics, kinetics, electrochemistry, transition metals, mechanisms, spectroscopy, acid-base equilibria, aromatic) + other 7 subjects (Physics has 1/many modules) — see uploads/curriculum-plan.md
- ⬜ TODO: review site content against exam board specs via BBC Bitesize science hub (https://www.bbc.co.uk/bitesize/subjects/zs6hvcw) — cross-check curriculum coverage & terminology against AQA/Edexcel/OCR etc.

## Known bugs / future updates (to fix)
(all four earlier items — nucleus cluster, intro visual, photon-jump animation, states-of-matter page — are DONE, see progress log)
- `public/electron-shells.dc.html` (+ deployed `.html`): add a visual at the top of the article — a labelled intro atom diagram (nucleus + shells) beside/under the hero — so the "How electrons live in energy levels" intro makes sense for readers who didn't arrive from the periodic table. Could reuse `<atom-3d>` with a caption/labels.
- `public/atom-3d.js`: nucleus is drawn as a single orange dot with the element symbol at centre. Should instead render a proton/neutron cluster (packed small spheres, two colors, count from atomic number/mass) at the centre; move the symbol label elsewhere (e.g. below the canvas). Affects periodic-table detail panel + electron-shells article.
- `public/electron-shells.dc.html` (+ deployed `.html`): add an animation showing an electron changing energy levels — absorbs energy → jumps to a higher shell, then falls back down → emits a photon (a little light-wave/flash carrying the extra energy). Fits section 04 (photon jumps). Build as a canvas/JS component (like `atom-3d.js`) or `React.createElement` animated element per DC animation rules; loop or play-on-click.
- New page: `public/states-of-matter.dc.html` — Field Guide 02: the four fundamental states of matter (solid, liquid, gas, plasma). Same article style as electron-shells (mono `// 0N` headers, Archivo/Space Grotesk/Plex Mono, warm paper). Explain particle arrangement/energy per state, transitions (melt/boil/ionize). Good candidates: animated particle-box demo per state; link from periodic table's state color-mode / temperature slider ("READ: STATES OF MATTER").

## Next ideas (not committed)
- Element "collection" progress (localStorage) — mark elements you've inspected
- Quiz difficulty levels (name→click, clue→click, symbol→name)
- Second module candidate: solar system to scale (Astronomy)
