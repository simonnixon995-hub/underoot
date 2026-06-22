# Underoot — store site

Static single-product store. No backend. Payment via Stripe Payment Link, fulfilment via Selfnamed (manual orders to start). Deploys to Cloudflare Pages with no build step.

---

## File map
```
index.html      → the product landing page (the whole sales page)
privacy.html    → Privacy Policy
terms.html      → Terms of Sale
refunds.html    → Refund & Returns Policy
shipping.html   → Shipping Policy
contact.html    → Contact / trader identity
legal.css       → shared styles for the 5 legal pages
reference/      → copy doc + image prompts (not part of the deployed site)
```
Footer links use `/privacy`, `/terms`, etc. Cloudflare Pages resolves these to the `.html` files automatically.

---

## TASK FOR CLAUDE CODE — replace every placeholder

Find-and-replace these tokens across all `.html` files:

| Token | Replace with |
|---|---|
| `[STRIPE_LINK]` | the Stripe Payment Link URL (appears on every Buy button in index.html) |
| `[TRADER_NAME]` | legal / sole-trader name |
| `[TRADER_ADDRESS]` | contactable UK address |
| `[CONTACT_EMAIL]` | a real, monitored email |
| `[DELIVERY_TIME]` | real UK delivery estimate confirmed by Selfnamed |
| `[DATE]` | today's date (on each legal page) |
| `[PRICE]` | retail price, e.g. £24 |
| `[WEEKS]` | how long one bottle lasts, e.g. 6–8 |
| `[X,XXX]` | real sales/customer count — **leave blank/remove until real** |
| `[SOCIAL_LINK]` / `[HANDLE]` | TikTok/IG link and handle |

Also in `index.html`:
- Replace the image placeholders (`.ph` blocks) with the real Selfnamed bottle image and the generated botanical images.
- Delete the three review cards in the Reviews section until real reviews exist (do not invent reviews).
- Remove the "small batch / when it's out it's out" line unless true.
- Paste the TikTok pixel into the marked `<head>` slot.
- Decide "Organic": the wordmark is just "Underoot" — only add "Organic" if the formula is certified.

Add (optional, nice to have): `favicon.ico`, `robots.txt`, `sitemap.xml`, Open Graph meta tags for link previews.

---

## MUST CONFIRM before publishing (do not publish these claims unverified)
- **Shipping page** says "nothing extra to pay on delivery" — only true if Selfnamed handles UK import VAT inclusively. Confirm in writing.
- **Privacy page** mentions EU transfer of delivery details — correct for Selfnamed EU fulfilment; keep accurate.
- **Responsible Person** — confirm whether Selfnamed or you hold the UK cosmetic Responsible Person duty (CPSR/SCPN). Not a website item, but required before selling.
- Legal pages are starting templates, not legal advice — review trader identity and refund terms against how you actually operate.

---

## Deploy (Cloudflare Pages)
1. Push this repo to GitHub.
2. Cloudflare dashboard → Pages → Create project → connect the repo.
3. Build command: none. Output directory: `/` (root).
4. Deploy → you get `underoot.pages.dev`. Point a custom domain at it when you have one.

## Go-live checklist
- [ ] Stripe account live + Payment Link created → pasted into all Buy buttons
- [ ] Selfnamed account + product + Underoot label + **design validation submitted**
- [ ] All placeholders replaced
- [ ] Real images in; fake reviews removed
- [ ] Legal pages reviewed; trader identity correct
- [ ] Deployed to Cloudflare Pages
- [ ] Store link in TikTok bio
