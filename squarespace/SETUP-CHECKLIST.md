# Rebuilding the WCCC design in Squarespace

Goal: match the new design while keeping **all content editable by staff in the normal Squarespace editor**.

Principle: put **content** in native blocks (staff edit these), and put **styling** in Site Styles + Custom CSS (set once, staff never touch).

---

## 1. Site Styles (do this first — it does ~70% of the work)

**Website → Site Styles**

### Fonts
- Headings → **Fraunces**, weight **600**
- Body / paragraph → **Nunito Sans** (regular 400, bold 700/800)
- Buttons → Nunito Sans, bold

### Colors (build a palette from these)
| Role | Hex |
|---|---|
| Text / ink | `#1F2933` |
| Primary (buttons, links) | `#0E7363`  (darker hover `#0A5749`) |
| Accent blue | `#15679D` |
| Accent coral | `#C2410C` |
| Accent plum | `#7A4EA3` |
| Light background 1 (cream) | `#FAF6EE` |
| Light background 2 (sand) | `#F3ECDF` |
| Light background 3 (sage) | `#EEF3EA` |
| Light background 4 (mist) | `#EAF1F5` |
| Dark sections / footer | `#1C2630` |

**Bright accents — DECORATION ONLY (icons, dots, shapes). Never use as text on white:**
teal `#2BB6A3` · blue `#38A8DF` · gold `#F4C41F` · coral `#F0663F`

> ⚠️ Accessibility: keep dark text on light backgrounds (and white text on the dark/teal/coral). Don't let an auto-generated section theme put a light bright color as text on white — that's what failed WCAG on the old site.

### Buttons & images
- Button shape → **Pill**
- Image corners → **Rounded** (~18px)

---

## 2. Custom CSS (set once)

**Website → Website Tools → Custom CSS** → paste the contents of `custom-css.css`.
Requires a paid plan above the entry tier.

---

## 3. Page layout (native sections — staff-editable)

Rebuild each page with standard sections. Pattern that recreates the look:

- **Hero:** full-width Image section using `assets/images/collage-hero.jpg` as the background, with a Text block (heading + paragraph + 2 buttons). For the "floating white card" effect, give that text area a white/cream section background and rounded corners.
- **Intro / curriculum / classroom rows:** alternating two-column sections (image left/text right, then flip). Use the reused photos from `assets/images/`.
- **Stats / commitments / values:** multi-column sections with an icon + heading + short text.
- **Testimonials:** 3-column section of quote text blocks on white cards.
- **CTA bands:** a section with the dark background `#1C2630`, white heading, and 2 buttons.
- **Footer:** Squarespace footer with the logo, link columns, contact info, and the land acknowledgement text.

Crank up **section top/bottom padding** — the generous whitespace is most of the Comet feel.

### Images to upload (from `assets/images/`)
`collage-hero.jpg` (header), `logo.jpeg`, `window-kids.jpeg`, `water-play.jpeg`,
`child-ball.jpg`, `climbing-wall.jpg`, `dahlias.jpg`, the five room photos
(`cloud/sunshine/rainbow/star/rocket-room`), `paris.jpeg`, `menu-april.jpg`.

---

## 4. The tuition table (the one special case)

Squarespace has no good native table. Add a **Code block** on the Enrollment page and paste
`tuition-table-codeblock.html`. It's styled to match and renders the three schedule columns.

**Staff editing:** to update tuition each year, edit the dates in the `<caption>` line and the
`$` amounts in the rows marked `<!-- EDIT PRICES -->`. That's the only spot in the whole site
that isn't pure point-and-click. (If you'd prefer, a plain Markdown block can hold a simpler
table — test whether your site renders Markdown tables; styling will be more basic.)

---

## 5. QA before launch
- [ ] Tab through each page with the keyboard — focus rings visible, links reachable.
- [ ] Check on a phone — sections stack, tuition table scrolls sideways.
- [ ] Confirm no light-colored text sits on a white background.
- [ ] Re-run a contrast checker (e.g. WebAIM) on any color combo you changed.
- [ ] Confirm the collage header crops well at mobile and desktop widths.
