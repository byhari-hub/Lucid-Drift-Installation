> **Usage:** This document is implementation-ready and functions as a secondary prompt. Paste it directly as system context for any AI coding or design assistant to reproduce this visual system faithfully.

---

## 1. Design Philosophy

This visual system is built on **editorial minimalism**: monochromatic, typographically-driven, with extreme whitespace as the primary compositional tool. Every decision prioritizes legibility over decoration. The design communicates structural restraint — the grammar of an archive that refuses to perform completeness.

**Core principles:**
- Absence over addition. No color, no borders, no dividers, no decorative elements.
- Weight and opacity encode hierarchy — not size alone.
- Grid and spatial rhythm carry all structure.
- Type is the visual. The letterforms are the design.

---

## 2. Typography System

### 2.1 Font Families

| Role | Font Family | Fallback Stack |
|---|---|---|
| **Display / Archive Statement / Body** | PP Nikkei Maru | `'PP Nikkei Maru', 'Inter', sans-serif` |
| **Phase Labels / Operative Grammar / Metadata** | Inter | `'Inter', 'Neue Haas Grotesk', 'GT America', sans-serif` |

**Rationale:**
- **PP Nikkei Maru** is a rounded geometric sans with neutral, open letterforms. Apply across all major typographic moments: archive statements, section headings, standard body paragraphs. Its softness at large sizes gives the display text warmth without sacrificing precision — appropriate for material that is felt before it is read.
- **Inter / Neue Haas Grotesk** handles all small-scale utility text — phase labels, theoretical reference indices, state identifiers, UI captions. These faces share PP Nikkei Maru's neutrality but carry sharper terminals suited to small optical sizes.

### 2.2 Type Scale

| Level | Font | Size (clamp) | Weight | Letter-spacing | Line-height | Usage |
|---|---|---|---|---|---|---|
| **Hero / Archive Statement** | PP Nikkei Maru | `clamp(40px, 5vw, 68px)` | 700 | `-0.02em` | `1.10–1.15` | Full-width conceptual declarations, manifesto-register project statements |
| **Phase Heading** | PP Nikkei Maru | `clamp(28px, 3.5vw, 44px)` | 700 | `-0.015em` | `1.15` | Phase and section headings (Phase 01, Phase 02, Phase 03) |
| **Statement / Highlight** | PP Nikkei Maru | `clamp(35px, 3vw, 40px)` | 400 | `-0.01em` | `1.25` | Mid-register paragraph statements on 4-column grid; alternating left/right alignment across 3-of-4 columns |
| **Body / Standard** | PP Nikkei Maru | `14px` | 400 | `0em` | `1.65` | Standard paragraph body text |
| **Phase Label / Operative Tag** | Inter | `11px` | 500 | `+0.13em` | `1.4` | ALL CAPS phase labels, operative grammar headers, column headers |
| **Theoretical / Metadata Body** | Inter | `13–13.5px` | 400 | `+0.01em` | `1.65` | Reference descriptions, state descriptions, technical note text |
| **Index / Mono** | Inter | `11px` | 400 | `0em` | `1.4` | Reference indices (T—01, T—02…), state numbers, figure labels |
| **Year / Trailing Meta** | Inter | `11px` | 400 | `0em` | `1.4` | Right-aligned publication years in reference tables |

### 2.3 Font Usage Rules

- ALL CAPS is used **exclusively** on labels at `11px` with Inter, never on body or display.
- `font-feature-settings: 'tnum' 1` must be applied to all numeric columns (index numbers, years) for aligned tabular figures.
- PP Nikkei Maru's rounded terminals mean display text should **not** use additional tracking — its natural spacing already reads well. Only tighten with negative tracking at large sizes (`-0.02em` at hero scale).
- Inter subheadings at `11px` require `+0.12–0.15em` letter-spacing to remain legible at small sizes.
- Active / current items: `font-weight: 700`, `color: #FFFFFF`
- Inactive / historical items: `font-weight: 400`, `color: rgba(255,255,255,0.38)`

---

## 3. Color System

### 3.1 Palette

| Token | Hex / Value | Usage |
|---|---|---|
| `--bg` | `#1C1C1C` | Full-page background, all sections |
| `--text-primary` | `#FFFFFF` | Active references, archive statements, bold labels |
| `--text-secondary` | `rgba(255,255,255,0.38)` | Inactive entries, column headers, phase labels |
| `--text-tertiary` | `rgba(255,255,255,0.22)` | Deeply muted metadata, figure captions |

**No accent color.** No borders. No dividers. No shadows. The system is intentionally 2-color. The monochromatic palette enacts the project's argument: the archive presents itself as complete, undifferentiated.

### 3.2 Color Logic by Component

| Component | Color | Opacity |
|---|---|---|
| Archive statement / hero text | `#FFF` | 100% |
| Active reference entry | `#FFF`, weight 700 | 100% |
| Inactive / historical entry | `#FFF`, weight 400 | 38% |
| Column headers ("PHASE", "AUTHOR", "YEAR") | `#FFF`, weight 500 | 38–40% |
| Index / reference numbers | `#FFF`, weight 400 | 38% |
| Year values | `#FFF`, weight 400 | 38% |
| Operative tags (ALL CAPS labels) | `#FFF`, weight 500 | 38–40% |
| Body / description text | `#FFF`, weight 400 | 100% |

---

## 4. Grid System & Layout

### 4.1 Global Layout Rules

```
Max content width:   1520px
Outer horizontal margin:  4vw (fluid, min ~48px on desktop)
Section vertical padding: 80–120px top and bottom
```

No horizontal rules, dividers, or border elements anywhere. All separation is achieved through whitespace.

---

### 4.2 Section-by-Section Grid Breakdown

#### Section A — Phase 01 / Archive Index (4-Column Table Grid)

Maps to the project's theoretical reference tables and operative grammar index — the formal record-keeping structures of the work.

```
Layout type: 4-column fixed-role table
Columns:     [Index] [Entry / Reference] [Empty/Spacer] [Year]
```

| Column | Role | Start Position | Alignment |
|---|---|---|---|
| Col 1 | Index (`T—01`, `T—02`…) | `~2% from left` | Left |
| Col 2 | Author / Entry name | `~25% from left` | Left |
| Col 3 | Empty spacer | `~50%` | — |
| Col 4 | Year | `~96–97% from left` | Right |

**Row specs:**
- Row height: `22–24px`
- No row borders or dividers
- Active rows: weight 700, full white
- Inactive rows: weight 400, `rgba(255,255,255,0.38)`
- Header row (`PHASE | AUTHOR | WORK | YEAR`) uses the same muted weight as inactive rows — it is structural, not dominant

**Header bar** (above reference list):
- 4-column rule repeated: `PHASE | AUTHOR | WORK | YEAR`
- Each column header aligns to the same start position as its data column
- No visual separation between header and rows

---

#### Section B — Phase 02 / Conceptual Framework (Hero + 2×2 Pillar Grid)

Maps to the project's theoretical positions and operative grammar — four core concepts arranged symmetrically below a full-width declaration.

```
Layout type:      Centered editorial with 2-column pillar grid
Hero behavior:    Full-width centered, with ~15% margin on each side
Pillar grid:      2 columns × 2 rows
```

**Hero Text Block:**
- Width: `~70% of viewport`
- Centering: Horizontally centered on the page
- Top margin from section start: `80px`
- Bottom margin before pillar grid: `80–100px`
- Font: PP Nikkei Maru, Hero scale, weight 700

**Pillar Grid:**

```
2 columns, equal width
Column width:   ~40% of viewport each
Gutter:         ~5% of viewport (~48–64px at 1400px wide)
Row gap:        40–48px between pillar rows
```

| Pillar | Position |
|---|---|
| Resistance | Col 1, Row 1 |
| Inherited Constraint | Col 2, Row 1 |
| Irreversibility | Col 1, Row 2 |
| Orphaned Archives | Col 2, Row 2 |

Each pillar:
- Title: Inter, `11px`, weight 500, ALL CAPS, tracking `+0.13em`
- Gap between title and body: `8–12px`
- Body: Inter, `13.5px`, weight 400, `line-height: 1.65`
- No wrapping box, card, or border — raw text block only

---

#### Section C — Phase 03 / System Architecture (Asymmetric Split Layout)

Maps to the installation's technical and spatial description — the declarative statement at left, the operative breakdown at right.

```
Layout type:    Asymmetric 2-zone composition
Zone 1 (Left):  Archive statement / system declaration, bleeding from left margin
Zone 2 (Right): 2-column operative grammar grid, right-aligned
```

**Zone 1 — Left-aligned Archive Statement:**
- Text starts at outer left margin (`~4vw`)
- Width: approximately `52–58% of viewport`
- Alignment: Ragged left, no centering
- Font: PP Nikkei Maru, Hero scale, weight 700, line-height `1.1`
- Top padding: `80–100px`

**Zone 2 — Right-anchored Operative Grid:**
- Right edge: flush to outer right margin (`~4vw from right`)
- Width: `~52% of viewport` (overlaps compositionally with Zone 1 below the declaration)
- Internal structure: 2 columns × 2 rows

```
Column width:   ~46% of Zone 2 each
Gutter:         ~8% of Zone 2
Row gap:        40–48px
```

| Pillar | Position |
|---|---|
| Audio — Granular Synthesis Engine | Col 1, Row 1 |
| Visual — Small Generative Model | Col 2, Row 1 |
| State — Stateless Control Layer | Col 1, Row 2 |
| Spatial & Interaction Design | Col 2, Row 2 |

**Compositional intent:** The left-heavy archive statement and right-anchored operative grid create a deliberate visual counterweight. The two zones do not share a baseline — the operative pillars sit in the lower half of the section, anchored to the bottom, while the statement occupies the upper-left. The asymmetry enacts the project's argument: archive and inheritance do not align.

---

#### Section D — Statement / Highlight (4-Column Alternating Grid)

Mid-register paragraph statements placed across multiple sections of the document. Each block occupies exactly 3 of 4 equal columns, with alignment alternating between instances to produce a diagonal visual tension — no two consecutive statements share the same anchor edge.

```
Layout type:    4-column equal grid, full content width
Column count:   4 × 1fr
Row gap:        clamp(48px, 6vw, 80px) between statement blocks
Font:           PP Nikkei Maru, 35–40px, weight 400 — uniform across all instances
```

**Column placement by instance:**

| Instance | Grid Column Span | Text Alignment | Anchor |
|---|---|---|---|
| 1st (odd) | `1 / span 3` | Left | Left edge |
| 2nd (even) | `2 / span 3` | Right | Right edge |
| 3rd (odd) | `1 / span 3` | Left | Left edge |
| 4th (even) | `2 / span 3` | Right | Right edge |
| …and so on | Alternates | Alternates | — |

**Typographic spec:**
- Font: PP Nikkei Maru, `clamp(35px, 3vw, 40px)`, weight 400 (uniform — no bold instances)
- Line-height: `1.25`
- Letter-spacing: `-0.01em`
- Color: `var(--text-primary)` — `#FFFFFF` at full opacity throughout
- No subheadings, no labels, no decorative elements

**Compositional intent:** The weight is held constant across all instances — hierarchy is produced purely through grid position and alignment direction, not typographic emphasis. The leftward blocks open the reading field; the rightward blocks close it. The one unused column functions as structural silence, equivalent to the absent remainder in the archive.

---

### 4.3 Spacing Tokens

```css
--space-section-v:       100px;   /* Top/bottom padding per section */
--space-hero-to-sub:     80px;    /* Archive statement bottom margin to next content block */
--space-pillar-gap-v:    48px;    /* Vertical gap between operative pillar rows */
--space-pillar-gap-h:    48–64px; /* Horizontal gutter between pillar columns */
--space-label-to-body:   10px;    /* Phase label to body text */
--space-outer-margin:    4vw;     /* Side margins, min 48px */
--space-statement-gap-v: clamp(48px, 6vw, 80px); /* Vertical gap between alternating statement blocks */
--max-width: 1520px;
```

---

## 5. CSS Custom Properties — Implementation Reference

```css
:root {
  /* Color */
  --bg:                #1C1C1C;
  --text-primary:      #FFFFFF;
  --text-secondary:    rgba(255, 255, 255, 0.38);
  --text-tertiary:     rgba(255, 255, 255, 0.22);

  /* Typography */
  --font-display:      'PP Nikkei Maru', 'Inter', sans-serif;
  --font-ui:           'Inter', 'Neue Haas Grotesk', 'GT America', sans-serif;

  --size-hero:         clamp(40px, 5vw, 68px);
  --size-heading:      clamp(28px, 3.5vw, 44px);
  --size-statement:    clamp(35px, 3vw, 40px);
  --size-body:         14px;
  --size-subheading:   11px;
  --size-pillar-body:  13.5px;
  --size-index:        11px;

  --weight-bold:       700;
  --weight-medium:     500;
  --weight-regular:    400;

  --leading-hero:      1.12;
  --leading-body:      1.65;

  --tracking-hero:     -0.02em;
  --tracking-label:    0.13em;
  --tracking-body:     0em;

  /* Layout */
  --max-width:         1520px;
  --outer-margin:      4vw;
  --space-section-v:        100px;
  --space-hero-to-sub:      80px;
  --space-pillar-gap-v:     48px;
  --space-pillar-gap-h:     clamp(32px, 4vw, 64px);
  --space-label-body:       10px;
  --space-statement-gap-v:  clamp(48px, 6vw, 80px);
}
```

---

## 6. Component Patterns

### Archive Statement (Hero Block)
```css
.hero {
  font-family: var(--font-display);
  font-size: var(--size-hero);
  font-weight: var(--weight-bold);
  line-height: var(--leading-hero);
  letter-spacing: var(--tracking-hero);
  color: var(--text-primary);
}
```

### Phase Label (Operative Tag / Subheading)
```css
.pillar-title {
  font-family: var(--font-ui);
  font-size: var(--size-subheading);
  font-weight: var(--weight-medium);
  letter-spacing: var(--tracking-label);
  text-transform: uppercase;
  color: var(--text-secondary);
  margin-bottom: var(--space-label-body);
}
```

### Operative Body (Pillar / Description)
```css
.pillar-body {
  font-family: var(--font-ui);
  font-size: var(--size-pillar-body);
  font-weight: var(--weight-regular);
  line-height: var(--leading-body);
  letter-spacing: 0.01em;
  color: var(--text-primary);
}
```

### Reference Row (Active)
```css
.client-row--active {
  font-family: var(--font-display);
  font-size: var(--size-body);
  font-weight: var(--weight-bold);
  color: var(--text-primary);
  font-feature-settings: 'tnum' 1;
}
```

### Reference Row (Inactive / Historical)
```css
.client-row--inactive {
  font-family: var(--font-display);
  font-size: var(--size-body);
  font-weight: var(--weight-regular);
  color: var(--text-secondary);
  font-feature-settings: 'tnum' 1;
}
```

### Standard Body Text
```css
.body {
  font-family: var(--font-display);
  font-size: var(--size-body);
  font-weight: var(--weight-regular);
  line-height: var(--leading-body);
  letter-spacing: var(--tracking-body);
  color: var(--text-primary);
}
```

### Statement / Highlight Block (Alternating 3-of-4 Columns)
```css
/* Container: full-width 4-column grid */
.statement-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: var(--space-statement-gap-v);
  padding: var(--space-section-v) var(--outer-margin);
  max-width: var(--max-width);
  margin: 0 auto;
}

/* Shared typographic spec — weight is uniform across all instances */
.statement-block {
  font-family: var(--font-display);
  font-size: var(--size-statement);   /* clamp(35px, 3vw, 40px) */
  font-weight: var(--weight-regular); /* 400 — no bold variation */
  line-height: 1.25;
  letter-spacing: -0.01em;
  color: var(--text-primary);
}

/* Odd instances: columns 1–3, left-aligned */
.statement-block:nth-child(odd) {
  grid-column: 1 / span 3;
  text-align: left;
}

/* Even instances: columns 2–4, right-aligned */
.statement-block:nth-child(even) {
  grid-column: 2 / span 3;
  text-align: right;
}
```

---

## 7. Grid Templates (CSS Grid)

### 4-Column Table Grid (Archive / Reference Index)
```css
.client-list {
  display: grid;
  grid-template-columns: 6% 44% 1fr auto;
  column-gap: 0;
  row-gap: 0;
  padding: 0 var(--outer-margin);
}
```

### 2×2 Pillar Grid (Centered / Conceptual Framework)
```css
.pillar-grid--centered {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: var(--space-pillar-gap-h);
  row-gap: var(--space-pillar-gap-v);
  max-width: 70%;
  margin: 0 auto;
}
```

### Asymmetric Split Layout (System / Phase 03 Section)
```css
.mission-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: 0;
  padding: var(--space-section-v) var(--outer-margin);
}

.mission-hero {
  grid-column: 1;
  align-self: start;
}

.mission-pillars {
  grid-column: 2;
  align-self: end;
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-gap: clamp(24px, 3vw, 48px);
  row-gap: var(--space-pillar-gap-v);
}
```

### Statement / Highlight Grid (4-Column Alternating)
```css
.statement-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: var(--space-statement-gap-v);
  padding: var(--space-section-v) var(--outer-margin);
  max-width: var(--max-width);
  margin: 0 auto;
}

/* Odd: 1 / span 3 — left anchor */
.statement-block:nth-child(odd)  { grid-column: 1 / span 3; text-align: left; }

/* Even: 2 / span 3 — right anchor */
.statement-block:nth-child(even) { grid-column: 2 / span 3; text-align: right; }
```

---

## 8. Responsiveness Notes

- Below `900px`: Collapse all multi-column pillar grids to a single column. Statement grid collapses to 2 columns; both odd and even blocks span `1 / span 2` (full width), reverting to left-align only.
- Below `680px`: Hero font reduces to a fixed `32px`; remove negative tracking. Statement blocks revert to `font-size: 28px`; grid collapses to 1 column, full-width, left-aligned.
- Reference index: On mobile, hide the index column; stack entry name and year on separate lines.
- Outer margin: Floor at `24px` on small screens.
- No breakpoint-specific color or font changes — the monochromatic palette requires no adaptation.

---

## 9. What to Exclude

The following are explicitly **not part of this system** and must not be introduced:
- Accent colors of any kind
- Borders, dividers, or horizontal rules
- Drop shadows, gradients, or blur effects
- Background cards or container surfaces
- Icon libraries or decorative imagery
- Hover animations beyond opacity transitions
- Rounded-corner UI components (cards, pills, badges)

---

*End of design system reference. This document is structured for direct reuse as an AI system prompt.*
