# Leva Sleep Email Build Standards

**Purpose:** the source of truth for building Leva Sleep campaign emails. Following it is what makes an email take about 5 minutes instead of 45, and what keeps the recurring mistakes from repeating. This doc lives in the repo so Claude reads it on every build, and it doubles as a shared reference for the team.

---

## 1. The offer: one source of truth, identical everywhere

The offer changes each event, but within a single email the **code and percentage must be identical in every location**: top banner, hero, body copy, every product pill, every CTA button, and the footer. Mismatched offers (one place saying `FLASH22 / 22%`, another saying `FLASHSALE / 12%`) were the single biggest source of edits, and a customer-facing error.

**Rule:** define the offer once at the start of the build, then use that exact code and number everywhere. Never let a second code or percentage slip in.

*Reference example:* code `FLASHSALE`, extra **12%** off, up to 72% off, ends Monday. (Always confirm the active code and percentage per event — do not assume.)

---

## 2. Pricing display

- Lead with the **monthly payment** (`$X/mo, $0 down`) as the largest price element on every product, every time.
- Show the total ("Total from $Y") and the strikethrough original as **secondary, smaller** text.
- Include the sale pill under each product: "Save [X]% with code [CODE]".

---

## 3. Links: verified URLs only

Every clickable element points to a real, verified URL. **Never invent a product URL.** Invented links are what broke "lots of the beds" last event.

**Standing pages (permanent):**

- Homepage: `https://www.levasleep.com/`
- Adjustable Bed Packages: `https://www.levasleep.com/collections/adjustable-bed-packages`
- Mattresses: `https://www.levasleep.com/collections/mattresses`
- Find a Store / showroom: `https://www.levasleep.com/pages/store-locator`

**Product URLs are event-specific.** Confirm each one against the live Shopify store before every build (Claude can pull and verify them). If a product has no confirmed URL, flag it rather than guessing.

*Past event products (verify before any reuse):*

- Beautyrest Limited Edition Split King: `/products/beautyrest-limited-edition-split-king-adjustable-bed`
- Stearns & Foster Estate Winslet Split King: `/products/stearns-foster-estate-winslet-split-king-adjustable-bed-package`
- Revive Split King: `/products/split-king-revive-adjustable-bed-package`

---

## 4. Images

- **Hosted image URLs only** (Shopify or Klaviyo CDN). Never base64 or "standalone" exports; they bloat the file past Gmail's clip limit and break.
- **No sale text baked into images.** No code, percentage, "SAVE BIG," urgency, or exclamation marks burned into a graphic. All promotional copy lives in editable HTML so it can be fixed without re-cropping. Use clean product and lifestyle imagery only.

---

## 5. Email-safe rendering (the `&check;` / `&starf;` lesson)

A **browser preview is not a real test.** Previews render in a browser engine; inboxes render in email clients with far less support. Something can pass in preview and break once it lands.

**Always send a live test to a real inbox (Gmail, Outlook, Apple Mail) before any send.** Use Klaviyo's "send test email." This is the gate that catches everything below.

**Special characters:**

- *Safe (widely supported):* `&rarr;` (→), `&rsquo;` ('), `&lsquo;` ('), `&ldquo;` / `&rdquo;` (" "), `&middot;` (·), `&ndash;` (–), `&hellip;` (…), `&nbsp;`.
- *Never use* exotic HTML5 entities like `&check;`, `&starf;`, `&star;`, `&hearts;`. They render in a browser but print as raw text in email clients.
- **For stars and checkmarks:** use a small **hosted icon image** (best, and the polished look Rik wants), or a **numeric reference** (`&#9733;` for ★, `&#10003;` for ✓), or the literal character in UTF-8. Never the named entity.
- Confirm `<meta charset="UTF-8">` is in the head, and use entities or numeric references rather than raw smart quotes, to avoid garbled "â€™" / "Ât'" text.

---

## 6. No internal titles visible

- Never let a working or file title (e.g. "Snoring Email 2") appear at the top of the email or anywhere a customer can see it. The first visible line is the sale banner.
- The `<title>` tag is **not** the subject line. Klaviyo ignores it. Set the subject in Klaviyo.

---

## 7. Footer and compliance

- Keep Klaviyo tags intact and as **valid working links**: `{% unsubscribe %}`, `{% manage_preferences %}`. Do not let style or attribute code leak into the visible text.
- Personalization: `{{ first_name|default:'there' }}`.
- A working unsubscribe link is a CASL requirement (Canada). Confirm it renders and works in the live test.
- Bake a hidden preheader into the HTML, and leave Klaviyo's preview-text field blank.

---

## 8. Brand voice and naming

- Premium-restrained tone. Sign-off sensibility: "Elevate yourself."
- **No em dashes. No exclamation marks.** Anywhere in copy, including inside images.
- **Always "Leva Sleep,"** never "Leva [anything]." For example "Leva Sleep couples," not "Leva couples."
- Colours: deep purple `#2D1B4E`, gold `#E8B547`, cream `#F5F1E8`.
- Keep a high human-touch feel. Polished, never "banged out."

---

## 9. Build hygiene

- **Table-based, email-ready HTML**, not a web app or "standalone" export. No `<script>` tags or loader bundles; email clients strip JavaScript.
- When pulling from Claude Design, ask for the **email-ready source as plain text**, not a standalone export.
- **Attribution:** if UTMs are baked into the HTML, turn Klaviyo's "add tracking parameters" OFF to avoid double-tagging. If there are **no** baked-in UTMs, leave Klaviyo tracking **ON** so you do not lose order attribution. Decide per event.
- **Naming convention:** `[M.D.YY] [Event] - Email [#] - [Segment]`, e.g. `[5.29.26] 72 Hour Sale - Email 1 - Snoring`.

---

## 10. Pre-send checklist

Run this before every send:

- [ ] Offer code and % identical everywhere (banner, hero, body, every pill, every CTA, footer)
- [ ] No back-end or internal title visible anywhere
- [ ] Images are clean (no baked-in sale text) and hosted (not base64)
- [ ] Stars and checks are images or numeric references, no `&check;` / `&starf;`
- [ ] All links verified (no invented URLs); unsubscribe and manage-preferences work
- [ ] Monthly payment leads on every product
- [ ] No em dashes, no exclamation marks; "Leva Sleep" used in full
- [ ] Live test sent to a real inbox and looks correct
- [ ] Saved as a draft for review, not scheduled or sent
