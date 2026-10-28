---
name: eamafia-brand
description: "Apply {{BRAND_NAME}} brand identity — navy and gold palette, Juana serif + Raleway type, gold script eA logo, warm EA-to-EA voice — to decks, docs, sheets, web pages, and mockups. Use for anything {{BRAND_NAME}}, {{SUB_BRAND_NAME}}, or {{EVENT_NAME}} branded."
---

<!-- exchange:setup -->
## Before you start
This has details to fill in. The first time it runs, ask the user for each one, then use the answer wherever its blank appears:
1. {{BRAND_NAME}}
2. {{SUB_BRAND_NAME}}
3. {{EVENT_NAME}}
4. {{BRAND_WEBSITE}}
5. {{LOGO_FILE_NAME}}
6. {{ORG_FACTS}}
7. {{FOUNDER_NAME}}
<!-- /exchange:setup -->

# {{BRAND_NAME}} Brand

Pulled from the live {{BRAND_WEBSITE}} design tokens (CSS custom properties and computed styles) on Oct 27, 2026. Hex values, font names, and sizes below are exact from the site. Anything marked *(suggested)* is a fallback, not {{BRAND_NAME}}'s own spec.

## Quick Reference

```
CORE COLORS
Navy / primary text    #083248   (headlines, nav, logo-adjacent text)   --blue / --text--primary
Gold                   #CE9851   (logo, buttons, underline swash, card accents)   --gold
Slate                  #375261   (CTA bands, dark sections)   --blue-secondary
Body text              #696969   (paragraphs, testimonials)   --text--secondary (dimgrey)
Background warm        #F1F2EF   (alternating sections, cards)   --background
Background             #FFFFFF

SUPPORTING
Teal                   #327397   (links, secondary data)   --teal
Polo blue              #85AAC9   (charts, soft highlights)   --polo-blue
Polo                   #E7EEF4   (pale blue tint, table bands)   --polo
Grey                   #CFD2D7   (dividers, borders)   --grey
Light text grey        #989898   (captions, meta)   --text-grey

TYPOGRAPHY
Display (H1–H3):  Juana 600 (licensed, Latinotype)
Body / UI:        Raleway 300/400/500/600/700 (Google Fonts)
```

## Core Principles

1. **Navy and gold, on warm white.** Navy carries the words, gold carries the brand (logo, buttons, one accent line). Warm off-white #F1F2EF keeps it soft rather than corporate.
2. **Serif for headlines, Raleway for everything else.** Juana at 600 for all headings; Raleway for body, nav, buttons, labels. Never set body copy in the serif.
3. **People first.** Real photography of EAs together at events carries the brand as much as the color does.
4. **Gold is the action color.** Primary buttons are always gold with white text. Don't spend gold on large backgrounds.
5. **Warm, peer-to-peer, polished.** Premium but welcoming, never stiff.

## Typography Spec (from {{BRAND_WEBSITE}})

| Role | Font | Size (web) | Weight | Line height | Color |
|---|---|---|---|---|---|
| H1 hero | Juana | 60.75px | 600 | 1.25 | #083248 (white on photos) |
| H2 section (large) | Juana | 54px | 600 | 1.25 | #083248 |
| H2 section | Juana | 43.875px | 600 | 1.1 | #083248 (white on slate) |
| Body large / intro | Raleway | 16.875px | 400 | 1.5 | #696969 |
| Body | Raleway | 13.5px | 400 | 1.5 | #696969 |
| Nav links | Raleway | 13.5px | 500 | — | #083248 |
| Button | Raleway | 16.875px (13.5px in nav) | 400–500 | — | #FFFFFF on #CE9851 |
| Testimonial name | Raleway | small | 600–700 | — | dark navy/grey |
| Testimonial title | Raleway | small | 400 | — | #696969 |

Headings use normal tracking (no letterspacing), no all caps. Button labels are Title Case ("Apply Now", "Learn More").

**Font fallbacks when Juana isn't installed** *(suggested)*: Fraunces 600 or DM Serif Display for web (Google Fonts); Georgia bold in Google Slides/Docs/Office. Raleway is free on Google Fonts, so always use the real one; if unavailable, Montserrat or Arial.

Scale down proportionally for slides and docs: keep H1 about 4.5× body and H2 about 3.25× body rather than the pixel values.

## Components

**Primary button:** solid gold #CE9851, white Raleway text, 6.75px corner radius (softly rounded, not a pill), ~12px × 20px padding, ~49px tall. No border, no shadow.

**Nav:** white bar, gold logo top left, navy Raleway 500 links on the right, gold "Apply Now" button last.

**Hero:** full-bleed event photo with a dark overlay, centered white Juana headline, white Raleway subhead below. Key words in the headline get a **hand-drawn gold underline swash** under them (e.g., under "by" and "For" in "Built by EAs. For EAs.").

**Split sections:** 50/50 photo + text blocks, alternating sides. Text side sits on #F1F2EF with a navy Juana heading, grey Raleway paragraph, and a gold button.

**Testimonial cards:** #F1F2EF card, square corners, with a solid gold offset bar along the bottom and right edge (like a hard gold drop-shadow). Grey Raleway quote, thin #CFD2D7 divider, round headshot, then bold name and grey title.

**CTA band:** full-width slate #375261 band, white Juana headline centered, gold button.

**Logo strip:** member company logos in a scrolling row, single-tone.

**Dividers:** 1px hairlines in #CFD2D7. Nothing heavy.

## Logo

- The mark is a gold handwritten script **"eA"** with a small dot after it (like a signature), #CE9851. It's a single-color mark: gold on white or light; white on navy, slate, or photos.
- No wordmark lockup is used in the site header; the script mark stands alone.
- Leave clear space around it at least 3× the height of the dot. Never redraw, stretch, outline, recolor (other than gold/white), or add effects.
- Placement: top left on title slides, document headers, and web nav. Keep it at least ~90px wide on screen.

**Logo SVG (exact from {{BRAND_WEBSITE}}, gold).** Save as `{{LOGO_FILE_NAME}}` when a file is needed; for a white version, change both `fill="#CE9851"` values to `#FFFFFF`.

```svg
<svg width="144" height="71" viewBox="0 0 144 71" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M130.214 32.7542L99.2724 37.0429C100.633 31.7938 102.28 26.6647 103.694 22.5628C104.842 19.368 105.982 16.3265 106.863 13.8654C106.923 13.692 106.983 13.5252 107.043 13.3585C108.33 9.7368 109.451 6.58199 110.304 3.91408C110.918 1.98651 105.735 1.41291 103.935 0.472469C102.127 -0.46797 99.9327 0.0322636 98.7055 1.64635C94.9037 6.64869 91.142 11.7311 87.5203 16.6267C82.3979 23.5366 77.062 30.6799 72.2064 36.8628C72.2064 36.8628 70.4189 39.0372 68.5714 41.2982L35.4626 45.887C37.1167 44.8599 38.4973 43.9795 38.9442 43.6593C51.6235 35.6089 63.9426 23.3832 67.8711 15.206C70.6457 9.42999 69.4251 5.57485 67.9111 3.34715C64.3895 -1.82194 52.7774 -0.341245 45.2738 3.41384C35.9628 8.07602 25.8381 19.4413 21.1226 32.5141C21.1226 32.5141 18.2679 38.3769 17.6276 45.6469C12.2117 48.1414 7.18938 49.7822 3.28089 50.0823C1.86689 50.189 0.666331 51.0761 0.146087 52.3834C-0.380826 53.7174 0.612972 55.6449 1.60677 56.7254C2.54721 57.7459 3.92119 58.1728 5.2418 57.866L18.4346 55.4582C19.5018 59.34 21.5694 62.9483 25.5246 66.0164C26.245 66.59 27.0053 67.1103 27.8057 67.5838C32.9748 70.6586 39.5845 71.6858 44.8403 70.3385C55.7854 67.5305 60.7277 61.7945 71.4861 48.1014L86.353 46.0404C84.6856 56.0251 85.4926 63.6954 90.7017 67.9974C93.0428 69.9383 95.9976 70.9121 99.6393 70.9121C106.649 70.9121 116.167 67.3504 128.753 59.9803C130.42 59.0065 130.974 56.8655 130 55.2047C129.026 53.5373 126.885 52.9837 125.225 53.9575C104.515 66.0898 101.8 63.1284 99.4458 61.1875C97.2915 59.4067 96.4711 56.1251 96.5912 51.8298C96.7512 49.5354 97.0981 47.0476 97.585 44.4864L131.194 39.8309C133.148 39.5574 134.516 37.7566 134.242 35.8023C133.969 33.8481 132.168 32.4808 130.214 32.7542ZM81.9443 34.8752C85.2392 30.5332 89.3878 25.5842 93.1295 20.7886C93.2163 20.6752 93.2963 20.5619 93.383 20.4485C91.909 24.7838 90.3883 29.3393 89.2344 33.3945C89.2344 33.3945 88.5608 36.0624 87.9338 38.6236L77.8624 40.0176C79.5499 37.89 81.4441 35.4955 81.951 34.8819L81.9443 34.8752ZM48.9956 8.60294C50.4496 7.87593 52.5839 7.00886 54.4715 7.00886C55.7587 7.00886 56.9393 7.41572 57.713 8.54958C58.5801 9.82351 58.1932 12.1846 57.4595 13.712C53.6044 21.7291 40.1781 33.1477 26.8786 40.778C27.739 27.6118 39.6512 13.2785 48.9956 8.60294ZM29.5665 53.9108L61.8016 49.4487C55.3586 56.3919 40.5116 69.1646 29.5665 53.9108Z" fill="#CE9851"/>
<path d="M140.118 31.1067C137.97 31.1067 136.236 32.8475 136.236 34.9885C136.236 37.1295 137.977 38.8703 140.118 38.8703C142.259 38.8703 144 37.1295 144 34.9885C144 32.8475 142.259 31.1067 140.118 31.1067Z" fill="#CE9851"/>
</svg>
```

For slides or docs that need a PNG, render this SVG (e.g., with cairosvg or rsvg-convert) at 2–4× size.

## Imagery

- **Event photography:** real EAs at {{BRAND_NAME}} events and the {{EVENT_NAME}}: workshops, conversations, laughing, writing on sticky notes. Warm natural light, candid, diverse group, shallow depth of field.
- Photos run full-bleed in heroes (with a dark overlay for white text) and edge-to-edge in 50/50 split sections.
- Headshots in testimonials are small circles.
- No stock-looking office imagery, no illustrations or icons as hero art.

## Voice & Messaging

**Tone:** warm, confident, peer-to-peer, empowering. Written by EAs to EAs: it sounds like a trusted colleague, not a vendor.

- **Headlines:** short, punchy, often two beats with periods ("Built by EAs. For EAs."). Section titles are one or two words in Title Case ("Memberships", "Summit").
- **Body:** plain and specific about outcomes: training, time-saving resources, high-quality connections, career growth, becoming a strategic partner.
- **Recurring themes:** community and belonging, peer learning (most of what members learn comes from other EAs), elevating the EA role, career growth, supporting top leaders in tech and VC.
- **Values (from {{BRAND_WEBSITE}}/about):** Authenticity, Purpose, Mastery, Impact.
- **CTAs (Title Case):** Apply Now, Learn More, Claim Your Spot, Subscribe.

**Brand names to use exactly:**
- **{{BRAND_NAME}}** — reproduce the brand name exactly as written in the setup value, including its capitalization and spacing. Never respace it, Title Case it, or set it in all caps.
- **{{SUB_BRAND_NAME}}** — reproduce exactly as written (the training/development brand; the site says the communities were unified under the {{BRAND_NAME}} name in June 2026, but {{SUB_BRAND_NAME}} still appears in nav and social).
- **{{EVENT_NAME}}** — the annual members-only summit ("The {{EVENT_NAME}}"), reproduced exactly as written.
- **EA / EAs** — always caps, plural with lowercase "s".

**Org facts (as listed on {{BRAND_WEBSITE}}):** {{ORG_FACTS}}. Re-check {{BRAND_WEBSITE}} before publishing any numbers or dates.

## Format-Specific Application

### Presentations
- Title slide: full-bleed event photo with dark overlay, white Juana title, gold logo top left. Or white slide with navy Juana title and a gold underline swash under one key word.
- Content slides: white or #F1F2EF background, navy Juana titles, Raleway body in #696969.
- Section breaks / closing: slate #375261 background, white Juana headline, gold accent.
- One gold accent per slide. Charts: navy #083248 primary series, then teal #327397, polo blue #85AAC9, gold #CE9851 for the highlight.

### Documents
- Juana headings in navy; Raleway body 10.5–11pt in #696969 (or navy for higher contrast in print).
- Gold for small accents only: a rule under the title, pull-quote bar, or highlighted callout border.
- Links in teal #327397. Hairline #CFD2D7 dividers.

### Spreadsheets
- Header row: navy #083248 fill, white bold Raleway (or Arial).
- Banding: #FFFFFF / #F1F2EF (or #E7EEF4 for a cooler band).
- Totals or key metrics: gold #CE9851 bottom border or text, never full gold row fills.

### Web, Mockups & Social
- White nav, gold logo, navy links, gold "Apply Now" button.
- Hero photo + white serif headline, 50/50 photo/text sections on #F1F2EF, testimonial cards with gold offset bar, slate CTA band.
- Social graphics: event photo with overlay or navy/slate background, white Juana headline, gold logo, one gold accent.

## Don'ts

- Don't use gold for large backgrounds or body text; it's for the logo, buttons, and accents.
- Don't set headings in Raleway or body copy in the serif.
- Don't use all caps for headlines (only the caps portions of the brand names are caps).
- Don't use pill-shaped or square-cornered buttons; use the soft 6.75px radius.
- Don't use pure black (#000000) for text; use navy #083248 or #696969.
- Don't redraw or restyle the "eA" script mark.
- Don't invent member stats, testimonials, or quotes from {{FOUNDER_NAME}} or members.
