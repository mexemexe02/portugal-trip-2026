# Plan: Professional HTML for All Portugal Trip Docs

## Goal
Turn all relevant .md files into professional, cohesive HTML with pricing, graphs, and navigation. One design system across the site.

---

## 1. Files to Create / Update

| HTML file | Source | Main content |
|-----------|--------|--------------|
| **index.html** | New (hub) | Trip title, fixed dates, cost range summary, nav to all pages, optional quick checklist |
| **itinerary.html** | ITINERARY.md | Flow, dates table, interactive checklist, accommodation |
| **flights-research.html** | FLIGHTS_RESEARCH.md | Itinerary summary, flight research sections, **cost snapshot + confirmed prices**, **bar charts** (cost by leg, total low/high), quick links (buttons), decisions |
| **full-plan.html** | FULL_PLAN.md | Options A–E at a glance, full text for each option, link to interactive options page |
| **portugal-trip-options.html** | Existing | Add nav bar and optional shared header/footer so it fits the set |

---

## 2. Design System (Shared)

- **Tone:** Refined travel planner – clear, professional, easy to scan. Not playful or generic “AI” gradient.
- **Typography:** One serif for headings (e.g. Fraunces or similar), one sans for body (e.g. DM Sans). Already used in options page; reuse.
- **Colors:** Warm neutrals (cream/off-white bg, dark text), one accent (terracotta/olive) for highlights and CTAs. Use CSS variables in a single `styles.css`.
- **Components:** Nav bar, page title + subtitle, cards for sections, styled tables, primary/secondary buttons, horizontal bar charts (CSS + minimal inline data).
- **Responsive:** Stack tables/cards on small screens; nav collapses or stays simple.

---

## 3. Pricing & Data to Include

- **From FLIGHTS_RESEARCH.md:**
  - Cost Snapshot table (per leg: YYZ→OPO, Train, LIS→FNC, FNC→YYZ, Total low/high).
  - Confirmed Flight Prices: YYZ→OPO by source; LIS→FNC by source; FNC→YYZ by source; Rough total low/high.
- **index.html:** One summary line or card: e.g. “Estimated total (flights + train): ~$1,030–2,020 CAD per person.”

---

## 4. Graphs / Visuals

1. **Cost breakdown by leg (flights-research.html)**  
   Horizontal bar chart: 4 legs (YYZ→OPO, Train, LIS→FNC, FNC→YYZ). Each bar shows range (low–high) or midpoint. Label in CAD. CSS: flex or width %; legend “Low” / “High” or single “Est. range.”

2. **Total cost range (flights-research.html or index.html)**  
   One bar or two bars: “Low total ~$1,030–1,385” and “High total ~$1,630–2,020” (or single range bar). Keeps focus on per-person total.

3. **Optional: YYZ→OPO by source (flights-research.html)**  
   Small horizontal bars: Expedia $601, Skyscanner $643, Google $684, etc. (round-trip). Build from Confirmed Flight Prices table.

All charts: CSS-only (no chart lib). Use `<div>` bars with width %, labels, optional `<figure>` + `<figcaption>`.

---

## 5. Navigation & Linking

- **Nav bar (all pages):** [Home] [Itinerary] [Flights & pricing] [Full plan (options)] [Compare options]. Same order everywhere.
- **index.html:** Cards or list with short description + “Open →” for each page.
- **full-plan.html:** Prominent link to **portugal-trip-options.html** (“Compare all options interactively”).
- External links (Google Flights, Expedia, etc.): `target="_blank"` and `rel="noopener"`.

---

## 6. Implementation Order

1. Create **styles.css** (variables, typography, nav, cards, tables, buttons, chart bars).
2. Create **index.html** (structure, nav, summary, cost range, links to other HTML).
3. Create **itinerary.html** (content from ITINERARY.md, checklist with JS).
4. Create **flights-research.html** (full content, pricing tables, 2–3 bar charts, quick links).
5. Create **full-plan.html** (options A–E, link to interactive comparison).
6. Update **portugal-trip-options.html** (add nav, optionally link to styles.css for consistency).

---

## 7. Checklist Before Done

- [x] All 5 HTML files exist and open without errors.
- [x] Nav works on every page.
- [x] Pricing appears in flights-research.html and summary on index.
- [x] At least 2 graphs: cost by leg + total range (in flights-research.html).
- [x] External links open in new tab (flights-research quick links).
- [x] Design is consistent (styles.css: fonts, colors, cards, tables).
- [x] Print-friendly: @media print in styles.css (hide nav, simplify).
