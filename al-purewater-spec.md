# A&L Pure Water — Website Design Spec

## Project brief

Static single-page informational website for A&L Pure Water, a small neighborhood water
store in Mountain View, CA. Owners are Ally & Lawrence. No backend needed. The site's
one job: give a first-time visitor everything they need to show up with their jugs.

Audience: Local families and regulars who refill large water containers. They want to
know what kind of water, how much it costs, where the store is, and when it's open.
That's it.

---

## Design direction: "Corner store, done beautifully"

Lean into the honest, neighborhood character of this place — a humble local staple with
loyal 10-year customers and an owner who personally answers every question. No wellness
startup vibes. No corporate water brand. Real, warm, and typographically sharp.

The design should feel like it was made with care *for this specific place*, not
assembled from a template.

---

## Token system

### Color palette

```
--color-bg:         #F7F6F2   /* warm off-white, like filtered light */
--color-surface:    #EEEBE3   /* slightly darker card/section bg */
--color-ink:        #1A1A18   /* near-black, warm not cold */
--color-ink-muted:  #6B6860   /* secondary text */
--color-accent:     #2D6A8F   /* deep water blue — the one color moment */
--color-accent-lt:  #E8F1F7   /* accent tint for backgrounds */
--color-rule:       #D4D0C8   /* dividers */
```

No gradients. No drop shadows. Flat and clean.

### Typography

- **Display:** `DM Serif Display` (Google Fonts) — used *only* for the hero headline and
  section eyebrows. Warm, has personality without being precious. Set large, with tight
  leading.
- **Body/UI:** `Inter` (Google Fonts) — for everything else: nav, body copy, prices,
  hours, labels. Set at 400 and 500 weight only. No bold except for prices/numbers.
- **Numerals:** Prices and pH values use `Inter` with `font-variant-numeric: tabular-nums`
  and slightly larger size — make the numbers feel like data, not decoration.

Type scale:
```
--text-xs:    0.75rem   /* labels, captions */
--text-sm:    0.875rem  /* nav, footnotes */
--text-base:  1rem      /* body */
--text-lg:    1.125rem  /* lead paragraph */
--text-xl:    1.375rem  /* subheadings */
--text-2xl:   2rem      /* section titles */
--text-hero:  clamp(3rem, 8vw, 6rem)  /* hero only */
```

### Signature element

The **pricing section** is the page's one designed moment: a comparison between
membership and per-gallon pricing rendered as a clean two-column "card pair" — almost
like a minimalist menu. Oversized numerals, light rule separating water types, a small
`[MEMBERSHIP]` badge in accent blue. This is the thing someone screenshots and texts
to a friend.

---

## Page structure

Single HTML file. Sticky nav with anchor links. No JavaScript frameworks — vanilla JS
only for smooth scroll and mobile menu toggle.

### 1. Nav
```
[ A&L Pure Water ]                    [ Water  Pricing  Hours  Find Us ]
```
- Logo/name left, links right
- Sticky on scroll, with a subtle `border-bottom: 1px solid var(--color-rule)` that
  appears on scroll (JS class toggle)
- Mobile: hamburger → full-screen overlay menu

### 2. Hero
```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│   Clean water.                                          │
│   Mountain View's                                       │  ← DM Serif Display, hero size
│   neighborhood source.                                  │
│                                                         │
│   Purified RO · Alkaline · Delivery · Kiosk 24/7        │  ← Inter sm, muted, spaced caps
│                                                         │
│   [ Find our location ]   ( 650 ) 938-3122              │  ← CTA + phone
│                                                         │
└─────────────────────────────────────────────────────────┘
```
- Full viewport height (100svh)
- Background: `--color-bg` (no image needed — the type carries it)
- A single thin horizontal rule above the tagline line
- The accent blue appears *only* on the CTA button and phone number

### 3. What we offer

Four items in a 2×2 grid (stacks to 1 col on mobile):

```
┌──────────────────────┐  ┌──────────────────────┐
│ Purified RO Water    │  │ Alkaline Water        │
│                      │  │                       │
│ Reverse osmosis      │  │ pH 8–10, minerals     │
│ filtered for clean,  │  │ added. Clean, crisp,  │
│ neutral taste.       │  │ deeply hydrating.     │
└──────────────────────┘  └──────────────────────┘
┌──────────────────────┐  ┌──────────────────────┐
│ Bottles & Supplies   │  │ Water Delivery        │
│                      │  │                       │
│ Wide selection of    │  │ Within 10 miles of    │
│ water bottles and    │  │ Mountain View. Call   │
│ purification systems.│  │ to set up service.    │
└──────────────────────┘  └──────────────────────┘
```
- Cards use `--color-surface` background, no border, generous padding
- Small all-caps eyebrow label above each card title in `--color-accent`
- No icons — just type

### 4. Pricing ← THE signature section

```
┌─────────────────────────────────────────────────────────┐
│  Pricing                                                │
│  ─────────────────────────────────────────────────────  │
│                                                         │
│   ┌───────────────────────┐  ┌───────────────────────┐  │
│   │   Per Gallon          │  │   Membership          │  │
│   │                       │  │  ┌─────────────────┐  │  │
│   │   RO Purified  $0.75  │  │  │   MEMBER PRICE  │  │  │
│   │   ───────────────     │  │  └─────────────────┘  │  │
│   │   Alkaline     $1.50  │  │                        │  │
│   │                       │  │  100 gal for  $70     │  │
│   │                       │  │  (RO Purified)        │  │
│   └───────────────────────┘  └───────────────────────┘  │
│                                                         │
│   Prices may vary. Call or visit to confirm.            │
└─────────────────────────────────────────────────────────┘
```
- Background: `--color-accent-lt`
- Price numerals: `--text-2xl`, `font-weight: 500`, `tabular-nums`
- `[MEMBER PRICE]` badge: small, `--color-accent` bg, white text, `border-radius: 2px`
  (almost no radius — keep it sharp)
- Thin `1px solid var(--color-rule)` between water types
- Disclaimer line in `--color-ink-muted`, `--text-xs`

### 5. How it works / Kiosk

Simple 3-step horizontal layout (stacks vertically on mobile):

```
  In-store           Outdoor Kiosk         Delivery
  Mon–Sat            Open 24 / 7           Within 10 mi
  ─────────          ───────────           ────────────
  Browse, fill,      Accepts bills         Call to
  and pick up        and credit cards.     set up.
  supplies.          Bring your jugs.
```
- No numbers (the steps aren't sequential, they're options)
- Thin vertical rules between columns on desktop
- Each option gets a one-word category label in accent blue, all-caps, `--text-xs`

### 6. Hours & Location

Two-column layout:

```
┌─────────────────────────┐  ┌─────────────────────────┐
│  Hours                  │  │  Find Us                │
│                         │  │                         │
│  Mon – Fri  10am – 6pm  │  │  1040 Grant Rd          │
│  Saturday   10am – 5pm  │  │  Suite 187              │
│  Sunday     Closed      │  │  Mountain View, CA      │
│                         │  │  94040                  │
│                         │  │                         │
│                         │  │  [ Get directions ↗ ]   │
└─────────────────────────┘  └─────────────────────────┘
```
- Hours table: `--text-base`, days in `--color-ink-muted`, times in `--color-ink`
- "Sunday Closed" — "Closed" in `--color-ink-muted` italic
- Google Maps embed below (or linked — embed can feel heavy for a simple site, either works)

### 7. Footer

```
──────────────────────────────────────────────────────────
A&L Pure Water  ·  1040 Grant Rd Suite 187, Mountain View
(650) 938-3122  ·  © 2025
──────────────────────────────────────────────────────────
```
- Single line, centered or left-aligned
- `--text-sm`, `--color-ink-muted`
- No social links (they don't have accounts we know of)

---

## Responsive behavior

- **Breakpoint:** 768px
- Nav collapses to hamburger at mobile
- Hero: type scale clamps naturally, CTA stacks under headline
- Offer grid: 2×2 → 1 col
- Pricing cards: side by side → stacked (per-gallon first)
- How it works: horizontal → vertical
- Hours/Location: side by side → stacked

---

## What needs real content from the owners

Mark these clearly as `[PLACEHOLDER]` in the code:

1. **Current prices** — Yelp data may be outdated, confirm with Ally
2. **Membership tiers** — there may be more options than we found
3. **Logo / wordmark** — do they have one? If not, the name set in DM Serif Display is
   fine as a logotype
4. **Store photos** — optional but high impact. Even one good shot of the kiosk or
   the bottles wall would elevate the site significantly
5. **Delivery details** — radius, minimum order, how to sign up

---

## Implementation notes for Claude Code

- Single `index.html` file with `<style>` block and `<script>` block inline
- Google Fonts loaded via `<link>` in `<head>`: DM Serif Display + Inter
- No CSS frameworks — write custom CSS using the token variables above
- JS: ~30 lines max — scroll-triggered nav border, mobile menu toggle, smooth scroll
- No animations except: nav border fade-in on scroll (CSS transition), and subtle
  `opacity: 0 → 1` on hero text on page load (single keyframe, `prefers-reduced-motion`
  respected)
- Accessible: semantic HTML (`<nav>`, `<main>`, `<section>`, `<footer>`), all links
  have descriptive text, phone number is an `<a href="tel:...">` link
- The Google Maps "Get directions" link should open in a new tab to Google Maps with
  the address pre-filled

---

