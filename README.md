# Handoff: Mr Levi's Legacy — website (Homepage, HEART Framework, Resources, Blog, About, FAQ, Contact)

## Overview
Mr Levi's Legacy is a compassionate education and support site for people who care for companion animals. The site is organised around the **HEART™ Companion Animal Care Framework** — five "Hubs" covering the stages of a companion animal's life. This bundle covers seven core pages plus one sample article template.

`About v2.dc.html`, `FAQ v2.dc.html` and `Contact v2.dc.html` were added after the original four-page handoff, using client-supplied copy (About and FAQ) and the established design tokens, shared components and interaction patterns below. All cross-page links (nav, footer, homepage cards, the "Visit our FAQ" prompt) have been rewired to point at these pages instead of the placeholder `#story` / `#join` anchors used while they didn't exist yet.

## About the design files
The `.dc.html` files in this bundle are **design references created in HTML** — prototypes showing intended look, copy and behaviour. They are not production code to copy directly. They use a small in-house runtime (`support.js`) with a custom `<x-dc>` template syntax; that runtime is **not** part of the deliverable.

The task is to **recreate these designs in the target codebase's environment** (WordPress theme, React, Astro, etc.) using its established patterns. If no environment exists yet, choose the most appropriate stack. Open each `.dc.html` in a browser to view the design; read the markup for exact values.

Notes for the implementer:
- Templates use `{{ value }}` holes and `<sc-for list="…" as="…">` / `<sc-if value="…">` blocks. Treat these as ordinary loops/conditionals in your framework.
- `style-hover="…"` is a hover-state attribute; convert to `:hover` CSS.
- `<helmet>` contains the head (font links, body reset). Everything else is inline styles.
- Page-to-page links are relative filenames (`Blog v2.dc.html`). Replace with real routes.

## Fidelity
**High fidelity.** Colours, typography, spacing and interactions are final and derived from the client's Figma file. Recreate pixel-accurately. Layouts are already responsive via `clamp()` and `auto-fit` grids — preserve that behaviour rather than hard-coding breakpoints.

Content width: all page content is centred in a **1084px max-width** container (header and hero use 1500px), with page padding `clamp(20px, 3vw, 40px)`.

---

## Design tokens

### Colour
| Token | Hex | Use |
|---|---|---|
| Navy deep | `#0A2E52` | Hero background, footer, headings, dark cards |
| Navy mid | `#0C3660` | Dark section band background |
| Navy link/primary | `#0E4478` | Buttons, links, card link text |
| Navy accent | `#21447B` | Modal primary button |
| Slate body | `#3D4A55` | Default body text |
| Slate muted | `#63727D` | Secondary body copy, eyebrows |
| Slate light | `#98A5AE` | Input placeholder |
| Grey on navy | `#B3BDC4` | Body copy on navy cards |
| Gold | `#C99A45` | Primary accent, rules, CTA button |
| Gold hover | `#D9A85D` | Gold button hover |
| Gold light | `#E4C791` / `#E3BE7C` | Eyebrow text on navy |
| Gold rule | `#C79449` | Hero divider rule |
| Gold text-on-gold-btn | `#3A2A0C` | Text colour inside gold buttons |
| Cream header | `#F8F3EB` | Sticky header background |
| Cream section | `#FBF8F2` | Alternating section background, input fill |
| Blue-grey band | `#EDF1F5` | Newsletter section background |
| White | `#FFFFFF` | Cards, alternating sections |
| Cream on navy | `#EFE3CB` | Hero italic sub-line |
| Pale blue on navy | `#CFDDEC` / `#E7EDF3` | Body copy on navy |

**HEART Hub accent colours** (the circular numbered badge on each hub card):
| Hub | Badge colour | Italic tagline colour |
|---|---|---|
| H — Home & Belonging | `#253E60` | `#253E60` |
| E — Enrichment & Living Well | `#93A389` | `#7C8C72` |
| A — Ageing, Adaptation & Advocacy | `#CAA355` | `#A9853F` |
| R — Reflection, Remembrance & Returning | `#C0896C` | `#A9714F` |
| T — Together, Through Every Stage | `#213858` | `#3D5A80` |

### Typography
Google Fonts:
```
Fraunces: ital,opsz,wght@0,9..144,300;0,9..144,400;0,9..144,500;1,9..144,300;1,9..144,400
Karla: wght@400;500;600;700
Newsreader: ital,opsz,wght@0,6..72,400;1,6..72,400
```
- **Karla** — UI, nav, body copy, eyebrows, buttons, inputs. Body default 17–17.5px / line-height 1.65–1.72.
- **Fraunces** (400, and 300 for the large pull-quote) — section headings, card titles, italic taglines and quotes.
- **Newsreader** (400 + italic) — the large page `<h1>` on interior pages (HEART, Resources, Blog) and their italic sub-line.
- The client's Figma uses **New Spirit** for the hero display face; it is not available as a web font, so **Fraunces/Newsreader stand in**. If the client licenses New Spirit, swap it in for the `<h1>` and section headings.

Scale (all `clamp(min, fluid, max)`):
| Role | Size | Family / weight | Other |
|---|---|---|---|
| Home hero h1 | `clamp(34px,4.2vw,52px)` | Fraunces 400 | lh 1.16 |
| Interior hero h1 | `clamp(36px,5vw,68px)` | Newsreader 400 | lh 1.08 |
| Interior hero sub | `clamp(18px,2.1vw,25px)` | Newsreader italic | lh 1.55 |
| Section h2 | `clamp(30px,3.4vw,42px)` | Fraunces 400 | lh 1.14, ls -0.504px |
| Hub card h2 | `clamp(24px,2.4vw,30px)` | Fraunces 400 | lh 1.18, ls -0.3px |
| Feature h3 | `clamp(26px,2.7vw,34px)` | Fraunces 400 | lh 1.14, ls -0.408px |
| Card h3 | 22px | Fraunces 400 | ls -0.264px |
| Manifesto pull-quote | `clamp(26px,3.1vw,38px)` | Fraunces 300 | lh 1.36, ls -0.57px |
| Body | 17 / 17.5px | Karla 400 | lh 1.65 / 1.72 |
| Small print | 13.5px | Karla 400 | |
| Eyebrow | 12px | Karla 700 | ls 2.4px, uppercase |
| Hero eyebrow (home) | 20px | Karla 700 | ls 4px, uppercase |
| Hero eyebrow (interior) | 13px | Karla 700 | ls 2.86px, uppercase |
| Button label | 15.5px | Karla 600 | |
| Nav link | 16px | Karla 400/500 | |

### Spacing & shape
- Section vertical padding: `clamp(56px,7vw,116px)` top / `clamp(50px,7vw,110px)` bottom.
- Grid gaps: 26px (card grids), 14px (gallery), 18px (hub chips), 12–16px (button rows).
- Radii: `999px` pills (buttons, inputs, tags) · `24px` large cards · `21px` resource cards · `18px` nav cards · `14px` gallery images · `10px` guide-cover thumbnail.
- Shadows:
  - Large card: `inset 0 0 0 1px rgba(14,68,120,0.07), 0 2px 4px rgba(10,46,82,0.04), 0 12px 32px rgba(10,46,82,0.07)`
  - Card on navy: `inset 0 0 0 1px rgba(14,68,120,0.08), 0 7px 45.6px rgba(0,0,0,0.22)`
  - Resource card: `0 0 26.2px 3px rgba(0,0,0,0.05)`
  - Guide cover: `inset 0 0 0 1px rgba(255,255,255,0.12), 0 18px 40px rgba(10,46,82,0.28)`
  - Input: `inset 0 0 0 1px rgba(14,68,120,0.2)` on `#FBF8F2` fill, 51px tall, 21px horizontal padding.
- Gold "hairline" rule motif: `64px × 1px`, `#C99A45` at `opacity: .45`, paired with an uppercase eyebrow.

---

## Shared components

### Header (all pages)
`position: sticky; top: 0; z-index: 40;` background `#F8F3EB`. Inner row max-width 1500px, padding `14px clamp(20px,3vw,40px)`, flex space-between, wraps.
- Logo `assets/fig-logo.png`, height 96px, links home.
- Nav (Karla 16px, colour `#0A2E52`): **Heart™** as a pill with `inset 0 0 0 1px rgba(212,166,78,0.45)` border, padding `14px 26px`, radius 999px (hover: border `#C99A45`); then About, Resources, Blog, FAQ, Contact as plain links, padding `14px 18px` (hover `#0E4478`); then **Join us** solid pill `#0E4478` / white, padding `15px 24px` (hover `#0A2E52`).

### Newsletter band ("Walk beside us") — homepage, HEART, Resources, Blog
Section background `#EDF1F5`, white card (24px radius, large-card shadow), padding `clamp(46px,5.4vw,84px) clamp(24px,4vw,60px)`, centred column.
Gold rule + eyebrow "JOIN US" + rule → h2 "Walk beside us." → 520px paragraph → email input + gold **Join us** button (`#C99A45`, text `#3A2A0C`, hover `#D9A85D`) → 13.5px reassurance line.

### Footer (all pages)
Background `#0A2E52`, padding `clamp(52px,5vw,79px) … 40px`. 1084px grid, `repeat(auto-fit, minmax(210px,1fr))`, 40px gap.
Columns: roundel image (152px wide) · **HEART Hub** (five hub links) · **Explore** (Framework, Resources, Blog, Shop (soon)) · **Connect** (About Mr Levi, Contact, FAQ, Join the community).
Column headings: Karla 700, 12px, ls 2.16px, uppercase, white. Links: 15.5px, `rgba(255,255,255,0.66)`, hover `#E4C791`.
Bottom bar: 28px top padding, `1px solid rgba(255,255,255,0.13)`, 13.5px: "© 2026 Mr Levi's Legacy™. All rights reserved." left, "Privacy · Terms · Made with heart by Creative Feed" right.

### Interior page hero (HEART / Resources / Blog)
Full-width navy photographic band with a dark overlay, centred column max-width 900px: gold eyebrow (13px, ls 2.86px, `#E3BE7C`) → Newsreader h1 in white → 72×1px `#C79449` rule → Newsreader italic sub-line in `#EFE3CB`.

---

## Screens

### 1. Homepage (`Homepage v2.dc.html`)
Purpose: orient a first-time visitor, explain HEART, capture an email.

Sections in order:
1. **Hero** — `min-height: clamp(460px,44vw,846px)`, full-bleed `fig-home-hero.jpg` (`object-position: 60% 45%`) under a left-to-right gradient `rgba(10,46,82,0.86) → rgba(10,46,82,0.62) 42% → rgba(255,255,255,0.05) 78% → rgba(255,255,255,0.55)`. Left-aligned 640px column: eyebrow "Mr Levi's Legacy™" → h1 "Wherever you are on the journey, *you're welcome here.*" → 430px paragraph → two pills: gold **Explore HEART™ →** and translucent-white **Join our community** (`rgba(255,255,255,0.24)` with a `rgb(194,194,194)` inset border).
2. **Story** (`#story`, background `#FBF8F2`) — two-column `auto-fit minmax(320px,1fr)`: left is eyebrow "IT'S ALL ABOUT HEART" + rule, h2, two paragraphs, and a blockquote with a `2px solid #C99A45` left border (Fraunces italic 20px, `#0E4478`); right is the 309px roundel with an "MR LEVI" caption (Karla 600, 12.5px, ls 2px).
3. **Free guide card** — centred logo, then a white 24px-radius card: `grid-template-columns: 190px 1fr`. Left is a 190×253px navy gradient "book cover" (`linear-gradient(154.942deg, #0E4478, #0A2E52)`) with "FREE GUIDE" eyebrow, Fraunces 21px title "The HEART Companion Reflection", and a 34px flourish. Right is eyebrow + h3 + paragraph + email input and navy **Send me the guide** button + "No spam, ever."
4. **"Where would you like to begin?"** — navy band (`#0C3660`) with `fig-band-bg.jpg` under `rgba(12,54,96,0.93)`. Centred rule/eyebrow/rule + h2, then a `auto-fit minmax(290px,1fr)` grid of six 18px-radius cards, each title / body / gold-navy link line. Five are white links (HEART™, Resources, Blog, About Levi, Contact); the sixth is a navy `#0A2E52` card with a `1px dashed rgba(255,255,255,0.47)` outline, "Shop", and a **COMING SOON** gold-outline pill. Below: "Looking for a quick answer? Visit our FAQ."
5. **Gallery** — cream section, eyebrow + h2 "The small, ordinary moments are the ones we keep." + paragraph, then a 4-column mosaic, `grid-auto-rows: clamp(96px,9.4vw,170px)`, 14px gap, 14px radii, with three span-2 tiles and three span-2-row tiles (see markup for exact placement). Caption below in Fraunces italic 15px.
6. **Manifesto** — white section, 724px column, centred logo (88px) and a Fraunces 300 statement with the second half in italic.
7. Newsletter band + footer (shared).

### 2. HEART Framework (`HEART Framework v2.dc.html`)
Purpose: explain the framework and its five Hubs.
1. Interior hero — "It's all about HEART."
2. **Intro** — eyebrow "A FRAMEWORK FOR EVERY STAGE" + heading + copy.
3. **Hub chip band** — navy band, centred heading + copy, then an `auto-fit minmax(190px,1fr)` grid of five hub chips linking down to each hub section.
4. **Five hub sections**, alternating white / `#FBF8F2`. Each opens with a 52px circular badge (hub accent colour, white Fraunces 26px letter H/E/A/R/T) beside an h2 and a Fraunces italic tagline in the hub's tagline colour, then descriptive copy and supporting cards.
5. Newsletter band + footer.

### 3. Resources (`Resources v2.dc.html`)
Purpose: list downloadable resources across two access tiers — genuinely free (no account) and member-only (free WordPress account required).
1. Interior hero — eyebrow "GUIDES & DOWNLOADS", h1 "Resources for every stage", sub-line explaining the two tiers.
2. An intro line above the grid spells out the tiers in plain language before the reader hits a single card.
3. **Resource grid** — cards (white, 21px radius, `0 0 26.2px 3px rgba(0,0,0,0.05)`, padding `26px 28px 28px`, `min-height: 272px`): a HEART-category pill (Karla 700, 12px, ls 1.2px, uppercase, tinted with that hub's colour) paired with an access-level label (`Free · no login` in sage `#6F8266`, or `Members` in slate `#98A5AE`), Fraunces 22px title (`#12304F`), 17.5px blurb (`#3D4A55`), and a footer row with the file type icon (PDF or XLS) and a download action whose label switches between "Download" and "Log in to download".
4. Newsletter band + footer.

**Access tiers.** This was a deliberate call, not a technical default: resources someone might need in a crisis — an emergency care plan, the Quality of Life Scale, comfort-care guidance, grief support, an emergency contact sheet — are free with no account at all, so nothing stands between a guardian and help in an urgent moment. Everything else (the "First 30 days", trackers, enrichment guides, reflection tools, etc.) sits behind a free membership. **Which specific resources landed in which tier is a starting proposal** — flag any you want moved before this goes live; it's a one-line change per resource (the `free: true/false` flag in the `RESOURCES` array).

**Member gate (the key interaction).** Clicking a free resource downloads immediately, no modal. Clicking a member resource while signed out opens a modal with three states:
- `viewLogin` — h2 "Welcome back", email + password fields, a "New here? Create a free account →" link into `viewRegister`.
- `viewRegister` — h2 "Create your free account", name + email + password fields, a "Already a member? Log in →" link back to `viewLogin`.
- `viewSuccess` — a 64px green-tinted circle (`rgba(147,163,137,0.18)` fill, `#6F8266` tick), h2 "Welcome, {name}" (or "You're signed in" for a returning login), "This device will remember you…", and a navy `#21447B` button that starts the pending download.

Production behaviour: standard WordPress accounts (`wp_insert_user()`, Subscriber role) — not a magic link. Register/login should hit WordPress's own auth (e.g. via the REST API or a lightweight AJAX handler), not a third-party service; on success set the normal WP logged-in cookie so the browser (and its password manager) carries the session on return visits, same as any other WP login. State needed client-side: `authView` (`login|register|success|null`), the pending resource, and a signed-in flag — the prototype simulates this with `localStorage`, which the real build replaces with checking the actual WP session. Validate email format and password length before enabling submit; show an inline error on failure.

### 4. Blog (`Blog v2.dc.html`)
Purpose: browse articles by HEART category.
1. Interior hero.
2. **Filter row** — solid uppercase letter pills (All, H, E, A, R, T) tinted with each hub's accent colour; the active pill is filled, inactive are outlined. Filtering is client-side over the post list.
3. **Post grid** — cards with category pill, Fraunces title, excerpt, and a read link.
4. Newsletter band + footer.

### 5. Article template (`Blog Article.dc.html`)
Sample article ("Reading the Signals") showing the long-form template: narrow measure body copy, paired relaxed/stressed **signal cards**, and tinted callout notes. Use as the pattern for all article detail pages. *Flagged for removal from the design set if the client doesn't want it — confirm before building.* Note: this file predates the "v2" pass and still links to non-`v2` filenames (`Homepage.dc.html`, `HEART Framework.dc.html`, etc.) — resolve that alongside the removal decision rather than patching it in isolation.

### 6. About (`About v2.dc.html`)
Purpose: tell Mr Levi's story and explain why the site exists, using the client's supplied About-page copy in full.
1. Interior hero — eyebrow "Mr Levi's Story™", h1 "One little dog. One extraordinary legacy.", italic sub "He loves. Faithfully. Wholeheartedly. Without expectation."
2. **Meet Mr Levi** — two-column intro (narrative text + sticky portrait image), matching the homepage Story section's layout, with a gold-bordered pull-quote for "He loves. / Faithfully. Wholeheartedly. Without expectation."
3. **A journey that began long before Levi** — narrow single-column narrative (the author's own story: childhood on a farm, becoming an End-of-Life Doula), followed by a full-width rounded photo with caption.
4. **The questions Levi helped me ask** — navy band (matches the HEART hub-chip band styling) listing the five guiding questions from the source copy as individual cards.
5. **Why Mr Levi's Legacy™ exists** / **The HEART™ behind everything we do** (with a CTA button into `HEART Framework v2.dc.html`) / **Our mission** (Fraunces 300 statement, matching the homepage Manifesto section) / **Looking forward** — narrow-column sections alternating white/cream, ending in a full-width photo + caption.
6. Custom join band — "Stay close to the journey." (client copy) instead of the generic "Walk beside us." heading, with two extra inline links to the HEART page and Resources page beneath the form, per the source doc's designer note.
7. Footer.

Designer's placement notes for the four unbriefed photos (hero, candid, nostalgic, tender closing) were mapped to existing `assets/` photography (`hero-beach-walk.jpg`, `levi-sweater-beach.jpg`, `jo-and-dogs.jpg`, `levi-railings.jpg`) — swap for the client's actual choices if they differ.

### 7. FAQ (`FAQ v2.dc.html`)
Purpose: answer the questions guardians ask most, organised into the five categories from the client's FAQ doc.
1. Interior hero — h1 "Answers, gently offered.", intro line linking to the Contact page.
2. **Accordion** — five categories (About Mr Levi's Legacy™, Using Our Resources, Support Guidance & Your Vet, Your Privacy & Our Content, Staying in Touch), each a white card of collapsible rows. One question open at a time; `+`/`−` indicator, same card-shadow language as the Resources cards. Built with the same `sc-for` / `sc-if` / `DCLogic` state pattern as the Resources page's email-gate modal — see the script block for the `FAQS` data array and `Component.toggle()`.
3. A gold-bordered callout with the source doc's professional-advice disclaimer.
4. Newsletter band + footer.

The source doc's internal links (About, HEART™, Contact) are wired to their pages; **Privacy Policy**, **Terms & Conditions** and **Refund Policy** are left as plain text — those pages don't exist yet in this bundle (see Outstanding, below), so no link target is invented for them.

### 8. Contact (`Contact v2.dc.html`)
Purpose: a way to reach the team — not present in the original four-page handoff, designed to match the rest of the system since every other page linked to it.
1. Interior hero — h1 "We're here, whenever you need us."
2. Two-column: a contact form (name, email, subject, message) on the left with client-shaped copy ("I read every message personally…", from the FAQ doc's "How do I contact you?" answer) and inline validation; on the right, an urgent-care redirect callout (matches the FAQ's "urgent help" guidance — this is not for emergencies), a direct email card, and a link into the FAQ.
3. Submitting swaps the form for a confirmation state, following the same non-functional-prototype convention as the Resources email gate — see README **Interactions & behaviour** below.
4. Newsletter band + footer.

---

## Interactions & behaviour
- **Header** sticks at `top: 0`, `z-index: 40`. No scroll-state change.
- **Hover states** are colour-only, no transforms. Buttons: navy `#0E4478 → #0A2E52`; gold `#C99A45 → #D9A85D`; footer/nav links → `#E4C791` or `#0E4478`. Add a `~150ms ease` colour transition.
- **Newsletter forms** (two on the homepage, one per interior page) are non-functional in the prototype. Wire to the client's email platform; on success replace the form with a confirmation line in place.
- **Anchor links** (`#story`, `#join`) scroll within the page — account for the sticky header with `scroll-margin-top`.
- **Responsive**: every grid is `repeat(auto-fit, minmax(Npx, 1fr))` and all padding/type uses `clamp()`, so the pages reflow without media queries. The one place to check is the homepage gallery — its 4-column mosaic should collapse to 2 columns on narrow viewports.
- **Accessibility**: decorative images carry empty `alt`; content images have descriptive alt text. Keep those. Check gold-on-navy and `rgba(255,255,255,0.66)` footer links against WCAG AA at their sizes.

## Assets
All in `assets/`, exported from the client's Figma file. **The images in this bundle have already been optimised** — photographs downscaled (heroes ≤2200px wide, all others ≤1400px) and re-encoded as JPEG at quality 0.82. Total asset weight is ~6 MB, down from ~83 MB of original Figma PNG exports. Logos, roundels, the flourish and the file-type icons remain PNG because they need transparency.

- `fig-logo.png` / `logo.png` — wordmark/lockup (rendered at 88–96px tall)
- `fig-roundel.png` / `levi-roundel.png` — illustrated portrait of Mr Levi on a gold roundel (309px story, 152px footer, 110px modal)
- `fig-flourish.png` — small gold ornament on the guide cover
- `fig-icon-pdf.png`, `fig-icon-xls.png` — resource file-type icons
- `fig-home-hero.jpg`, `fig-hero-bg.jpg`, `fig-heart-hero.jpg`, `hero-beach-walk.jpg` — hero photographs
- `fig-band-bg.jpg` — texture behind the navy "Find your way" band
- `fig-g1.jpg`, `fig-g2.jpg`, `fig-g3.jpg`, `fig-g5`–`fig-g12.jpg` — homepage gallery photographs
- `fig-heart-e/r/t.jpg`, `levi-*.jpg`, `jo-and-dogs.jpg`, `puppy-pot.jpg`, `cattle-dog-toy.jpg` — HEART hub and article photographs
- `fig-blog-1.jpg`, `fig-blog-2.jpg` — blog card photographs

For production, serve WebP/AVIF with JPEG fallback and add `srcset` for the heroes. Photographs are the client's own; no stock licensing applies. Original full-resolution exports remain in the client's Figma file if larger sources are ever needed.

## Files in this bundle
| File | Contents |
|---|---|
| `Homepage v2.dc.html` | Homepage |
| `HEART Framework v2.dc.html` | HEART Framework page |
| `Resources v2.dc.html` | Resources page + email-gate modal |
| `Blog v2.dc.html` | Blog index with category filter |
| `Blog Article.dc.html` | Article detail template |
| `About v2.dc.html` | About / Mr Levi's Story page |
| `FAQ v2.dc.html` | FAQ page with category accordion |
| `Contact v2.dc.html` | Contact page + form |
| `support.js` | Prototype runtime — **not** for production |
| `assets/` | All images and icons |

## Outstanding before launch
1. WordPress member accounts (name/email/password, Subscriber role) wired to real registration/login — see **Access tiers** under Resources. Membership itself is free for now; a paid tier via WooCommerce checkout is a later phase, not this one.
2. Confirm the free-vs-member split on the Resources page — the `RESOURCES` array's `free` flags are a proposed starting point, not a final content decision.
3. Real resource list and real blog posts (current titles and copy are representative).
4. Confirm whether New Spirit will be licensed for display type.
5. Shop is "coming soon" — the card is a placeholder with no destination.
6. Contact form has no backend — wire it to real email delivery (see **Interactions & behaviour**).
7. Privacy Policy, Terms & Conditions and Refund Policy pages are referenced (FAQ page, footer) but not yet designed — the FAQ page leaves those mentions as plain text until they exist.
8. About page's four unbriefed image placements were filled with existing `assets/` photography as placeholders — confirm with the client whether those choices should be swapped.
