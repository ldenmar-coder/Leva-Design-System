# Leva Sleep Email QA Checklist

The single pre-send QA checklist for Leva Sleep emails. (Merged from the two earlier checklist versions — review in inbox, not just preview.)

---

## 1. Offer and promotion

- [ ] Discount percentage matches the campaign brief
- [ ] Promo code is correct and identical throughout the email
- [ ] Promo code matches banner graphics
- [ ] Promo code matches the CTA section
- [ ] Correct sale/event name appears throughout
- [ ] Sale end date is correct
- [ ] Sale end time is correct
- [ ] Countdown language matches the actual promotion timeline
- [ ] No old promo codes, discounts, or event names remain from previous campaigns

*Common errors found:* `FLASH22` showing instead of `FLASHSALE`; old sale graphics reused.

---

## 2. Product display

- [ ] Monthly payment shown first
- [ ] Monthly payment amount is correct
- [ ] Total price shown second and correct
- [ ] Savings displayed correctly
- [ ] Product names correct
- [ ] Featured products match approved campaign products
- [ ] Product images correct and match the products shown
- [ ] Links point to the correct products

**Preferred price format:**

```
AS LOW AS
$89/mo
Total from $4,499
Save 12% with code FLASHSALE
```

---

## 3. Brand voice

- [ ] "Leva Sleep" used consistently throughout
- [ ] No references to "Leva" alone where the brand name should be used
- [ ] Messaging feels human and premium
- [ ] No obvious AI language
- [ ] Headlines sound customer-focused
- [ ] Tone matches approved Leva Sleep campaigns
- [ ] CTA wording follows approved style

Avoid: "Leva Couples", "Leva Customers". Use: "Leva Sleep Couples", "Leva Sleep Customers".

---

## 4. Copy review

- [ ] No spelling mistakes
- [ ] No grammar mistakes
- [ ] No duplicated text
- [ ] No placeholder copy
- [ ] No internal notes visible
- [ ] No backend naming visible

Examples to catch: ❌ "Snoring Email 2" ❌ "Couples Campaign Final" ❌ "Draft Copy"

---

## 5. Images and graphics

- [ ] All images load
- [ ] All images use publicly accessible URLs
- [ ] Hero image contains the correct offer, discount, and promo code (if any is shown)
- [ ] No outdated sale information or old promo codes inside graphics
- [ ] Hero image does not cover or obscure the headline
- [ ] Text remains readable over images
- [ ] Mobile image review complete
- [ ] Desktop image review complete

*Common error found:* hero image obscuring headline.

---

## 6. Testimonials

- [ ] Testimonials display correctly
- [ ] Names display correctly
- [ ] No broken symbols
- [ ] No HTML code visible

Check specifically for raw `☆`, `✓`, or HTML entities showing as text. Should render as ★★★★★ and ✓ (use image icons or numeric references, not named entities).

---

## 7. HTML and technical

- [ ] No broken HTML
- [ ] No raw code visible
- [ ] No escaped entities visible (e.g. `&check;`, `&starf;`)
- [ ] No style/attribute code leaking into visible text (e.g. `STYLE="COLOR:#B8A8D4"`)
- [ ] Buttons render correctly
- [ ] Footer renders correctly
- [ ] Links render correctly
- [ ] Dynamic variables populate correctly
- [ ] No backend/internal titles visible to customers
- [ ] Preheader text configured correctly
- [ ] Subject line configured correctly (in Klaviyo, not the `<title>` tag)
- [ ] Preview text configured correctly

---

## 8. Links

- [ ] Hero CTA works
- [ ] Product CTAs work
- [ ] Sale CTA works
- [ ] Showroom links work
- [ ] Footer links work
- [ ] Unsubscribe works
- [ ] Manage Preferences works

---

## 9. Mobile review

Open the test email on a phone.

- [ ] Headline visible
- [ ] Images scale correctly
- [ ] Buttons visible
- [ ] No overlap issues
- [ ] No clipping
- [ ] Footer displays correctly
- [ ] Product cards display correctly

---

## 10. Desktop review

Open the test email on desktop.

- [ ] Hero section looks correct
- [ ] Product sections look correct
- [ ] CTA buttons aligned
- [ ] Footer displays correctly
- [ ] No spacing issues

---

## 11. Segment and send settings

- [ ] Correct audience selected
- [ ] Correct segment selected
- [ ] Correct exclusions applied
- [ ] Smart Sending settings verified
- [ ] Campaign scheduled correctly

---

## 12. Final approval

- [ ] Test email sent
- [ ] Reviewed in inbox (not just preview)
- [ ] Reviewed on mobile
- [ ] Reviewed on desktop
- [ ] Promo code verified one final time
- [ ] Sale dates verified
- [ ] Links verified one final time
- [ ] Approved by Matt (if required)

---

## Mandatory final question

Before scheduling, ask:

> "Is there anything in this email that could make a guest think this was copied from a previous campaign?"

If yes, fix it before sending.
