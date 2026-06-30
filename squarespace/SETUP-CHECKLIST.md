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

### Buttons
- Shape → **Pill**
- **Primary** button → green fill `#0E7363`, white text (hover `#0A5749`)
- **Secondary** button → blue fill `#15679D`, white text (hover `#0F4D77`)
- *(We recently changed the secondary button from coral/red to blue — make sure the secondary style is blue, not red.)*

### Colors (build a palette from these)
| Role | Hex |
|---|---|
| Text / ink | `#1F2933` |
| Primary (green — buttons, links) | `#0E7363` (hover `#0A5749`) |
| Secondary (blue) | `#15679D` (hover `#0F4D77`) |
| Accent coral *(small accents only — eyebrow labels, dots, icon tiles)* | `#C2410C` / text `#9A330A` |
| Accent plum | `#7A4EA3` |
| Light background — cream | `#FAF6EE` |
| Light background — sand | `#F3ECDF` |
| Light background — sage | `#EEF3EA` |
| Light background — mist | `#EAF1F5` |
| Light background — blush | `#F7EEF0` |
| Dark sections / footer | `#1C2630` |

**Bright accents — DECORATION ONLY (icon blobs, dots, sparkles). Never as text on white:**
teal `#2BB6A3` · blue `#38A8DF` · gold `#F4C41F` · coral `#F0663F` · rose `#9C2F63` on `#F7DFEA`

> ♿ Accessibility: keep dark text on light backgrounds (and white text on green/blue/dark). Don't let an auto-generated section theme put a light bright color as text on white — that's what failed WCAG on the old site.

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
- **CTA bands:** a section with dark background `#1C2630`, white heading, and 2 buttons (light + blue).
- **Footer:** Squarespace footer with the logo, link columns, contact info, and the land-acknowledgement text.

Crank up **section top/bottom padding** — the generous whitespace is most of the feel.

---

## 4. The tuition table (Enrollment page)

Squarespace has no good native table. Add a **Code block** on the Enrollment page and paste
`tuition-table-codeblock.html`. It's self-contained (its own styles) and renders the three schedule columns.

**Staff editing:** to update tuition each year, edit the dates in the `<caption>` line and the `$` amounts in the rows marked `<!-- EDIT PRICES -->`. That's the only spot on the interior pages that isn't pure point-and-click.

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

### Option B — Self-contained code-block homepage (most faithful)
Put the real homepage markup + scoped CSS into **one Code block** on a blank homepage. Pixel-matches the preview (hero, squiggles, hand-drawn icons, ribbon). Trade-off: edits to that page (e.g. a new testimonial) mean editing HTML inside the code block, not point-and-click. The homepage changes rarely, so this is often an acceptable trade.

> **I can generate the Option B code block(s) for you** from the current site — just ask. (It needs a small `<filter id="sketch">` SVG snippet added via Code Injection → Footer for the hand-drawn icon texture; I'll include that too.)

**Recommended:** interior pages native (Section 3) + homepage via **Option B** if you want it to match the preview, or **Option A** if staff will frequently rewrite the homepage.

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
