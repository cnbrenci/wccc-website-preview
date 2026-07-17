# Rebuilding the WCCC design in Squarespace

Goal: match the new design while keeping **content editable by staff in the normal Squarespace editor** wherever practical.

Principle: **content** lives in native blocks (staff edit these); **styling** lives in Site Styles + Custom CSS (set once, staff never touch).

> ⚠️ **Read this first — what's easy vs. hard.**
> The **interior pages** (Curriculum, Classrooms, Enrollment, Kitchen, Careers, About, Calendar, FAQ, Contact) are standard image/text/column layouts — they rebuild cleanly as **native Squarespace sections** and stay fully staff-editable.
> The **homepage** is now custom: an immersive collage hero with an overlaid card, a hand-drawn "squiggle/circle" treatment on keywords, hand-drawn (wabi-sabi) SVG icons in the promises section, and a sentence-style stats "ribbon." **None of those map to native Squarespace blocks.** See **Section 5** for the two ways to handle the homepage.

---

## 1. Site Styles (do this first — ~70% of the look)

**Website → Site Styles**

### Fonts
- Headings → **Fraunces**, weight **600**
- Body / paragraph → **Nunito Sans** (regular 400, bold 700/800)
- Buttons → Nunito Sans, bold

### Buttons (shape only)
- Shape → **Pill**, bold text.
- **Button _colors_ are set inside each color theme** (see below), not here — Squarespace ties button color to the section's color theme.

### Colors — Squarespace's model (5 base colors → themes → per-section)

Squarespace works in three steps, so set it up in three steps:

#### Step A — Set the 5 base palette colors
**Site Styles → Colors → Edit Palette.** Enter these five:

| Slot | Color | Hex |
|---|---|---|
| 1 | White | `#FFFFFF` |
| 2 | Ink (near-black) | `#1C2630` |
| 3 | Green (primary) | `#0E7363` |
| 4 | Blue (secondary) | `#15679D` |
| 5 | Cream | `#FAF6EE` |

Squarespace auto-generates 10 themes from these. **Don't worry about how the auto-generated themes look** — you'll override the specifics in Step B.

#### Step B — Customize the themes you'll actually use
**Site Styles → Colors → click a theme → set each item.** You need **one dark theme** and a handful of **light themes** that differ only by background color.

**Every LIGHT theme uses these same settings** — only the Section Background changes:

| Theme item | Value |
|---|---|
| Section Background | *(per theme — table below)* |
| Heading (all sizes) | `#1F2933` |
| Paragraph (all sizes) | `#1F2933` |
| Primary button — fill / text | `#0E7363` / `#FFFFFF` |
| Secondary button — fill / text | `#15679D` / `#FFFFFF` |
| Links | `#0A5749` |
| Text Highlight | `#0E7363` |
| Section Divider / Stroke | `#E6DED0` |
| Background Overlay, Inset Border | none |

Then give each light theme its own **Section Background**. You only *need* White + Cream + Sage; add the others where a section calls for it:

| Assign to a theme slot | Section Background | Used for |
|---|---|---|
| "White" (e.g. Lightest 1) | `#FFFFFF` | default content sections |
| "Cream" (e.g. Lightest 2) | `#FAF6EE` | page heros, alternating rows |
| "Sage" (e.g. Light 1) | `#EEF3EA` | highlight / "at a glance" bands |
| "Mist" (e.g. Light 2) | `#EAF1F5` | optional blue-tint band |
| "Blush" (e.g. Bright 2) | `#F7EEF0` | optional (kitchen allergy section) |
| "Sand" (e.g. Bright 1) | `#F3ECDF` | optional warm band |

> Since you fully control each theme, it's fine to repurpose a "Bright" slot as a soft tint — the slot names don't matter, only the values you set.

**The DARK theme** (assign to e.g. Darkest 1) — for CTA sections and the footer:

| Theme item | Value |
|---|---|
| Section Background | `#1C2630` |
| Heading (all sizes) | `#FFFFFF` |
| Paragraph (all sizes) | `#D6DDE2` |
| Primary button — fill / text | `#FFFFFF` / `#1C2630` |
| Secondary button — fill / text | `#15679D` / `#FFFFFF` |
| Links | `#FFFFFF` |
| Section Divider / Stroke | `#33414C` |

#### Step C — Assign a theme to each section
Select a section → **Colors** → pick the theme:

| Section | Theme |
|---|---|
| Page hero (eyebrow + H1 + lead) | Cream |
| Content rows | alternate White ↔ Cream (or White ↔ Sage) |
| "At a glance" / ratios / highlight bands | Sage |
| CTA bands ("Come see us in person", etc.) | **Dark** |
| Footer | **Dark** |

> ♿ Accessibility: these recipes keep dark text on light backgrounds and white text on dark — all WCAG AA. When editing a theme, never leave a Heading/Paragraph set to a light or bright color on a light background (that's what failed on the old site).

> 🎨 The **bright decorative hues** (teal `#2BB6A3`, blue `#38A8DF`, gold `#F4C41F`, coral `#F0663F`, rose `#9C2F63`) and the **coral eyebrow accent** (`#9A330A`) live *inside* the homepage code block and your uploaded icons — they are **not** section themes, so you don't need palette slots for them.

> **Note:** the homepage (Option B code block, Section 5) carries its own colors internally, so these themes mainly drive the **interior pages**.

### Images
- Image corners → **Rounded** (~18–28px)

### Header / nav
- Nav is just the page links (Home, Curriculum, Classrooms, Enrollment, Kitchen, Careers, About, Calendar). **No "Schedule a Tour" button in the header** — we removed it; the calls-to-action live in the page content instead.

---

## 2. Custom CSS (set once)

**Website → Website Tools → Custom CSS** → paste the contents of `custom-css.css`.
Requires a paid plan above the entry tier.

---

## 3. Interior pages (native sections — staff-editable)

Rebuild each with standard sections:

- **Page hero:** a cream-background section with an eyebrow (small H4), an H1, and a lead paragraph.
- **Two-column rows:** alternating image/text (image left, then flip). Use photos from `assets/images/`.
- **Stat / value / icon rows:** multi-column sections with an emoji or uploaded icon + heading + short text.
- **CTA bands:** two options — (a) a full-width section set to the **Dark** color theme (§1 Step C) with a white heading + 2 buttons (simplest), or (b) for the design's *floating rounded dark card*, use the `cta-card-codeblock.html` Code block on a light-themed section (Squarespace can't make a rounded inset card natively).
- **Footer:** Squarespace footer with the logo, link columns, contact info, and the land-acknowledgement text.

Crank up **section top/bottom padding** — the generous whitespace is most of the feel.

---

## 4. Tables (Code blocks) + the calendar image

Squarespace has no good native table, so each table is a **Code block** — add one to the page and paste the whole file. Each is self-contained (its own scoped styles, so it can't be broken by the theme) and scrolls sideways on small phones.

| Page | Code block file | Renders |
|---|---|---|
| Enrollment | `tuition-table-codeblock.html` | tuition by classroom × 3 schedules |
| Classrooms | `ratio-table-classrooms-codeblock.html` | room · ages · children · ratio |
| Curriculum | `ratio-table-curriculum-codeblock.html` | classroom · stage · ratio |

**Staff editing:** to update numbers later, edit the values inside the block's markup (for tuition, the rows marked `<!-- EDIT PRICES -->`). The colored dot before each room is set inline (`style="background:#RRGGBB"`).

Also on the **Calendar page**: upload `calendar-2025-2026.png` as an Image block (re-export and swap it each school year).

---

## 5. The homepage — pick one approach

The homepage has custom flourishes (immersive hero card over the collage, squiggle/circle keyword annotations, hand-drawn icons, sentence "ribbon" stats). Choose how much fidelity vs. editability you want:

### Option A — Simplified native homepage (most editable)
Rebuild with native sections and **drop/replace the custom flourishes**:
- Hero → full-width collage image section with a heading + 2 buttons on a cream card.
- Stats → a normal text line or a small column row (no hand-drawn circle/squiggle).
- Promises → native icon-cards using **emoji** or **uploaded icon images** (the hand-drawn SVGs won't transfer).
- Testimonials → native quote/text cards.
Result: looks close, fully staff-editable, but loses the hand-drawn personality.

### Option B — Self-contained code-block homepage (most faithful) ✅ ready to use
The whole homepage is prepared for you in **`homepage-codeblock.html`**. It pixel-matches the preview (immersive hero, squiggles, hand-drawn icons, ribbon stats) and is fully self-contained — all CSS is scoped under a `.wh` wrapper so it can't collide with Squarespace, and the hand-drawn icon filter is embedded (no Code Injection needed).

**To use it:**
1. Edit the homepage → add a **section**, set it to **full width** with **zero padding** (so the design can span edge-to-edge).
2. Add a single **Code block** to that section.
3. Open `homepage-codeblock.html`, copy **everything**, and paste it into the Code block. Save.
4. **View it on the live/preview site, not just the editor** — Squarespace's editor sometimes doesn't fully render code blocks.
5. **Images:** it currently loads images from the preview site so it works immediately. For a permanent site, upload the photos to Squarespace and replace every `https://www.cassibrenci.dev/wccc-website-preview/assets/images/` with your Squarespace image URL (find-and-replace inside the block).

**Editing content later:** the text (headings, paragraphs, the four testimonials) lives in the markup below the `</style>` line — search for the words you want to change. Not point-and-click, but the homepage changes rarely.

**Recommended:** interior pages native (Section 3) + homepage via **Option B** (`homepage-codeblock.html`). Use **Option A** instead only if staff will frequently rewrite the homepage themselves.

---

## 6. Images to upload (from `assets/images/`)
- `collage-hero.jpg` — homepage header crop (deskewed). `collage-deskew.jpg` is the full flat master if you want a different crop.
- `logo.jpeg` — full logo lockup (use in footer).
- `logo-mark.png` — the colorful "W" mark only (use in header next to the name).
- `calendar-2025-2026.png` — calendar page image.
- Photos: `window-kids.jpeg`, `water-play.jpeg`, `child-ball.jpg`, `climbing-wall.jpg`, `dahlias.jpg`, the five room photos (`cloud/sunshine/rainbow/star/rocket-room`), `paris.jpeg`, `menu-april.jpg`.

---

## 7. QA before launch
- [ ] Tab through each page with the keyboard — focus rings visible, links reachable.
- [ ] Check on a phone — sections stack, tuition table scrolls sideways.
- [ ] Confirm no light-colored text sits on a white background.
- [ ] Confirm primary buttons are green and secondary buttons are blue (no leftover red).
- [ ] Re-run a contrast checker (e.g. WebAIM) on any color combo you changed.
- [ ] Confirm the collage header crops well at mobile and desktop widths.
