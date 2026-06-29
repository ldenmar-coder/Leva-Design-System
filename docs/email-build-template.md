# Leva Sleep — Sale Email Build Template

A reusable scaffold for multi-email sale campaigns, extracted from the 72-Hour Sale handoff and made offer-agnostic. The offer is a placeholder here: set `{{CODE}}` and `{{PERCENT}}` once per event and apply them identically everywhere (see Email Build Standards, section 1). Do not hard-code a promo code into this template.

> Note: this template carries the *structure and per-segment voice*, not the copy of any one past campaign. Always pull live products, prices, and URLs per event.

---

## Build approach

**Path A:** email-ready HTML in the sale aesthetic, with **one commissioned hero PNG per email** at the top. Everything else is HTML/CSS. No standalone exports, no JavaScript.

---

## Shared design system (sale / promo aesthetic)

This is the heavy purple-neon sale aesthetic — distinct from the lavender/white editorial system used in the welcome-flow campaigns.

**Color palette**
- Page background: `#1a0f2e` (deep purple-black)
- Card frame background: `#2D1B4E` (primary purple)
- Hero band: gradient or solid `#6B2FD1` (neon purple)
- Body text on dark: `#ffffff`
- Body text in cards: `#2a2a2a` on `#ffffff`
- Accent neon (headline numbers): `#C9AAE9` → `#E0B0FF`
- Countdown band background: `#C9AAE9`
- Primary CTA pill: `#ffffff` background, `#2D1B4E` text
- Product card: `#ffffff` with subtle purple border

**Typography**
- Font stack: `'Helvetica Neue', Helvetica, Arial, sans-serif`. All sans-serif.
- No italics anywhere (one documented exception: a single quoted question, if the campaign calls for it).
- H2 (sub-hero): 32px bold, white
- H3 (section headers): 24px bold, white or `#2D1B4E` per background
- Body: 16–17px, line-height 1.5
- Eyebrow pills: 11px uppercase bold, letter-spacing 1.5px, white on `#2D1B4E`
- CTA pills: 16px bold uppercase, letter-spacing 1px, border-radius 30px, padding 16px 36px

**Buttons**
- Primary CTA: white fill, `#2D1B4E` text, no border, radius 30px
- Secondary CTA: transparent fill, 1px white border, white text

**Constraints**
- 600px single-table layout, inline CSS, table-based, Outlook-safe
- Klaviyo Liquid: `{% unsubscribe 'Unsubscribe' %}` and `{% manage_preferences 'Manage Preferences' %}`
- No wrapper `<a>` tags around tables — inline `<a>` on individual elements only
- No internal review/meta title at the top of the file
- Safe entities only (`&middot;`, `&rarr;`, numeric refs for ★/✓) — never `&check;` / `&starf;` (see Email Build Standards, section 5)
- Mobile-responsive

---

## Shared structure (identical scaffold across all emails in a campaign)

1. **Logo header** — white logo on `#2D1B4E`, centered, ~140px, padding 24px 0
2. **Hero image** — commissioned PNG, ~600×400, one unique hero per email, alt text per email
3. **Countdown band** — `#C9AAE9` background, Sendtric countdown image (unique URL per send/end-time)
4. **Opening text block** — the personalization slot; the main block that changes per segment. `#2D1B4E` bg, white text, 17px, line-height 1.6, padding 32px 40px
5. **Primary CTA pill** — centered, white fill, e.g. "USE CODE {{CODE}} AND SHOP NOW `&rarr;`"
6. **Product cards** — 3 stacked white cards: image, title (H3), monthly-payment-led pricing, 2-line blurb, "PLUS {{PERCENT}} OFF WITH CODE {{CODE}}" sub-pill; whole card links to verified PDP
7. **Showroom band** — white card, eyebrow "VISIT A SHOWROOM", H3 + body per email, secondary CTA to store-locator, city list
8. **Footer P.S. band** — `#2D1B4E`, "P.S." bold + per-email message
9. **Trust band** — "Hassle-Free Delivery `&middot;` 60 Night Trial `&middot;` 25-Year Warranty `&middot;` Made In Canada"
10. **Footer logo + unsubscribe** — smaller white logo, tagline, `levasleep.com`, Liquid unsub/manage links, event-specific sale-terms line

---

## Per-segment voice notes

**Snoring** — Matt's personal voice, letter format, warm but direct. Relational cost (the partner kept awake, drift to separate bedrooms) is the emotional lever. Not clinical. Never promise to cure snoring.

**Back Pain** — Brand voice (not Matt). Practical, empowering. Reader has tried mattresses, toppers, chiropractors — reframe the category ("you don't need a new mattress, you need a new position"). Never promise to cure back pain (regulatory). No aging identity. Not hospital-equipment vibe.

**Couples** — Matt's personal voice, letter format. Lead with and neutralize the objection ("isn't it split down the middle?" → "no, it's one continuous bed"). Keep canonical lines exact; never use "two halves" (use "two adjustable sides"). Hero must show the couple touching, not separated.

**Family / Closer** — Brand voice (not Matt). Direct, urgent, no fluff. Breadth of selection is the pitch ("largest selection of adjustable beds in Canada"). Works as the last-day closer: multiple urgency triggers, span the price range across the 3 product cards, lead with a phone-call CTA where relevant.

---

## Per-email checklist

- [ ] Section 1 — logo header on dark bg
- [ ] Section 2 — hero PNG renders, alt text in place
- [ ] Section 3 — Sendtric countdown loads, URL correct for this email's end time
- [ ] Section 4 — opening text block has the segment-specific copy
- [ ] Section 5 — primary CTA clickable, URL correct
- [ ] Section 6 — 3 product cards, prices match Shopify, links to verified PDPs
- [ ] Section 7 — showroom band, H3 + body correct, secondary CTA links
- [ ] Section 8 — P.S. band correct
- [ ] Section 9 — trust band entities render
- [ ] Section 10 — footer logo, Liquid unsub links correct, sale terms readable

---

## Klaviyo pre-save check

- [ ] Click-test every CTA (primary, secondary, product cards, any phone CTA)
- [ ] `{% unsubscribe %}` and `{% manage_preferences %}` render as links
- [ ] No wrapper `<a>` tags around tables; no internal meta title
- [ ] Sendtric countdown URL matches this email's end time
- [ ] Hero alt text in place
- [ ] Mobile preview: hero scales, opening text readable, product cards stack, CTA pills don't break across lines
- [ ] Subject + preview not truncated in Gmail / Apple Mail / mobile

---

## Cross-email check (before first send of a campaign)

- [ ] All emails feel like one sequence, not disconnected sends
- [ ] Hero design language consistent across the set
- [ ] `{{CODE}}` spelled identically in every email
- [ ] Sale end date appears identically in every footer
- [ ] Showroom city list identical in every email
