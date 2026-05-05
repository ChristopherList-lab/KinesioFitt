# Kinesio Fitt — Project Context

This file is for picking up future sessions cold. If you're an AI helping me, read this first.

## What this is

A rebuild of [kinesiofittmason.com](https://www.kinesiofittmason.com/) — a family-owned, full-service gym in Mason, TX. The original is a single-page anchor site that hides everything that makes the gym worth choosing. We replaced it with an editorial, conversion-focused homepage and (eventually) a multi-page sitemap.

Current state: **homepage only, single `index.html`, Tailwind via CDN, no build step.**

## The business

- **Name:** Kinesio Fitt
- **Address:** 310 Fort McKavitt St, Mason, TX 76856 (NW corner of the historic square)
- **Phone:** (325) 294-4300
- **Owner:** Ubaldo. He's also a working physical therapist and treats members on the floor. This is the brand's biggest differentiator and is reflected in the "Meet Ubaldo" section.
- **Member portal:** GymMaster — `https://kinesiofitt.gymmasteronline.com/portal/login`
- **Google reviews:** 5.0 stars, 8 reviews

### Hours

| | Gym | Kids Club |
|---|---|---|
| Sun | 1–6 PM | 1–6 PM |
| Mon–Thu | 5:30 AM – 9 PM | 8 AM – 7 PM |
| Fri | 5:30 AM – 5 PM | 8 AM – 4 PM |
| Sat | Closed | Closed |

### Classes (real, on the source site)

Body Strength, Vinyasa Hot Yoga, Group Weight Training, Pilates, Zumba & Strong, Mobility & Stretch, Butts and Guts, 30 Min Cardio, Full Body Circuit, Body Cardio & Conditioning.

### Pricing (what we have)

- Day pass: $10
- 2-day: $15 · 1-week: $30 · 2-week: $40
- 10-class pack: $75
- 4-week student: $45
- $50 one-time joining fee, **waived for military**
- Member tiers exist (Individual / Couple / Family / Senior) but **monthly rates are not yet known.** Owner needs to provide.

### Amenities

Free weights, machines (Cybex), spin studio (Life Fitness IC), group fitness studio, sauna, kids club with climbing wall.

## Brand system

Locked decisions, do not break:

### Colors
- `#0A0A0A` ink (primary)
- `#1E6BFF` cobalt (accent — pulled from the new chrome KF logo, **not** the old petrol/teal blue)
- `#0B2E66` cobalt-dark (hover/depth)
- `#FAF8F5` off-white (background)
- `#F0EDE8` concrete (alt background)
- `#D6D2CB` warm-sand (hairlines)
- `#6B6B6B` mute (secondary text)

### Type
- Display: **Space Grotesk** bold, all-caps, tight tracking
- Body: **Inter**
- Mono: **JetBrains Mono** for metadata, labels, timestamps, addresses (this is the modern signature, use it everywhere small text appears)

### Logo
- Use `Horizontal RGB.avif` for the wordmark in nav
- The chrome/cobalt monogram lives on the brand mark only — never apply gradients to type, buttons, or backgrounds
- Old logo (`KFitLogo_BEFORE.png`) is kept for reference; do not use

### Voice rules (per global CLAUDE.md)
- Active voice. Short sentences. Two-item lists.
- No em dashes. No adverbs (really, just, simply, truly).
- No "Welcome to our gym," no "We pride ourselves," no "Join our family."
- Direct. Local. Anti-fitness-jargon. State facts, skip justification.

### Layout / motion
- Editorial / Tracksmith reference. Asymmetric grids. Hairlines instead of cards-with-shadows.
- Sharp 90° corners (buttons may be 2px max).
- No carousels. No three-column feature blocks. No drop shadows. No gradients except on the logo mark.
- Subtle motion only: hero ken-burns, marquee scroll (pauses on hover), button label/arrow swap, scroll-reveal on key blocks, gentle drift on closing CTA. No parallax, no scroll-jacking.

## File map

```
/
├── index.html                  # the entire site
├── PROJECT.md                  # this file
├── README.md                   # GitHub-facing
├── Hero02.jpg                  # ✅ ACTIVE hero (night exterior, landscape)
├── HERO_IMG.jpg                # alternate hero (also night exterior)
├── Horizontal RGB.avif         # ✅ ACTIVE wordmark in nav
├── UbaldoHeadshot_AI.jpg       # ✅ ACTIVE Ubaldo portrait (black bg, branded polo)
├── KidsFit.jpg                 # ✅ ACTIVE kids climbing wall photo
├── ModernLogo.png              # 21MB hi-res logo (NOT in repo, kept locally)
├── ModernLogo.jpg              # logo reference, not used on site
├── KFitLogo_BEFORE.png         # old logo, reference only
├── web-photos/                 # ✅ ACTIVE — converted from /Photos DNG
│   ├── IMG_1831.jpg            # main floor wide
│   ├── IMG_1834.jpg            # Cybex row warm
│   ├── IMG_1835.jpg            # Cybex close-up
│   ├── IMG_1837.jpg            # spin bikes (amenities)
│   ├── IMG_1838.jpg            # spin bikes alt (gallery)
│   ├── IMG_1840.jpg            # group fitness studio (editorial)
│   ├── IMG_1841.jpg            # sauna (amenities)
│   ├── IMG_1844.jpg            # free weights / wood wall (amenities)
│   ├── IMG_1845.jpg            # heavy bag + Rogue rack (editorial)
│   ├── IMG_1848.jpg            # apparel display (gallery)
│   ├── IMG_1851.jpg            # signage close-up dusk (gallery)
│   └── ...                     # other shots not currently used
└── Photos/                     # raw DNG originals — NOT in repo
```

### Photo orientation gotcha
iPhone DNGs had EXIF orientation = 6. After converting via sips, the pixel data was already upright (1800×2400) but the EXIF tag was still set to 6, so browsers double-rotated and showed photos sideways. Fixed by stripping the orientation tag in PIL. **If you add new photos, run them through the orientation fix or verify with `python3 -c "from PIL import Image; print(Image.open('x.jpg').getexif().get(0x0112))"` — should return `1`.**

## What's on the homepage now

In order top to bottom:

1. **Top nav** — sticky, off-white, logo + nav + Login (GymMaster) + Free Day Pass CTA
2. **Hero** — Hero02.jpg with horizontal gradient overlay, hero copy on the dark left side
3. **Marquee** — cobalt strip with scrolling key facts
4. **Intro** — two-col with intro headline + paragraph
5. **Proof points** — Family Owned · Full Service · Open Early
6. **Editorial spread** — 3-up vertical photos (The Floor / The Studio / The Desk)
7. **Meet Ubaldo** — portrait + copy + pulled testimonial
8. **Classes** — indexed list + Membership teaser (day pass + 10-class pack)
9. **Amenities** — Free Weights · Spin · Sauna 3-up
10. **Inside the Gym gallery** — 6-up small photo grid
11. **Kids Club** — copy + hours + KidsFit climbing wall photo
12. **Reviews** — 5 real Google reviews + cobalt CTA card to Google Maps
13. **Visit** — contact info + hours + live Google Maps embed
14. **Closing CTA** — JOIN THE TEAM full-bleed cobalt
15. **Footer** — 4-col with NAP, nav, social, newsletter
16. **Mobile sticky CTA** — bottom bar, lg:hidden

### Free Day Pass modal
Triggered by any element with `data-day-pass`. Captures name / phone / email / DOB. Currently logs to `console.log()`. **TODO:** wire to a real endpoint (GymMaster lead API, Mailchimp, Formspree, or a Zapier webhook to email Ubaldo).

### Schema
HealthClub JSON-LD with founder (Ubaldo), aggregateRating (5.0 / 8), and the three displayed reviews. Once deployed and indexed, star rating can show in Google search results.

## What's NOT done yet

In rough priority order:

1. **Wire the day-pass form to a real endpoint** — currently logs to console
2. **Get monthly membership prices from Ubaldo** — biggest gap; blocks the Membership page
3. **Get a class schedule grid** (day × time) — blocks the Classes detail page
4. **Confirm Ubaldo's full name + credentials** (DPT? PT? where he trained?)
5. **Action photo of Ubaldo on the floor** — currently only have the studio headshot
6. **Build the rest of the sitemap:** /classes, /membership, /kids-club, /trainers, /about, /guest-passes, /contact, /shop
7. **Extract design system into a shared partial** so other pages stay consistent
8. **Real Google Place ID** for the maps links (currently using a search query URL)
9. **Deployment** — domain, hosting, DNS
10. **Analytics** (GA4 or Plausible)
11. **OG / Twitter card images**
12. **Favicon set**

## Development

```bash
# Local preview server
cd /Users/listmediagroup/Desktop/Claude_Knesiofitt
python3 -m http.server 8910
# then open http://localhost:8910/index.html
```

Hot tip: **always use a port ≠ 8000/8080** — those collide with other Python servers commonly running on the machine.

## Pricing for the gym owner

Recommended quote for what's been built: **$1,500–$2,500** with a goodwill structure (footer credit, three named local intros with a 60-day deadline, a written testimonial, permission to use as a portfolio piece). Don't go free; charge a token. See conversation history for full reasoning.
