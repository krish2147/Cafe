# Design Package — After Dunes Cafe

Tier 1, single continuous hero shot. Written before any generation. This document is the build's input.
Every line of viewer-facing copy below ships verbatim.

Not part of the deploy folder. Never zipped.

---

## 1. The brand premise

One word: **After**.

The name already says it. The dunes go gold, the sun drops behind the ridge, and the part worth
staying for begins. After work. After dinner. After the movie. After every other cafe in Alkapuri
has stacked its chairs. After Dunes pours from 8 in the morning until 2 at night, seven days a week,
and that hour range is the only thing on the page that needs defending, explaining, or selling.

Every section serves that one word. The hero crosses a ridge into lamplight. The signature element is
a dial of the day that the visitor runs down with their own hand. The menu section exists because the
reviews say people cannot tell what they are getting, and a cafe that is honest about its portions at
1am is a cafe you trust at 1am. If a section does not serve "after," it does not belong on the page.

**The research this is built on.** 4.4 from 211 ratings. Ambience 4.5, Service 4.5, Food 4.2.
The room and the people are what works. The repeated complaint, in the buyers' own words, is
"no images and quantity available in the menu," "very less quantity," and "prices are a bit overpriced
for the quantity." The site answers that objection head on with pictures and portions, and sells the
two things that genuinely score: the room, and the hours.

**The single call to action:** Book a table. Every section funnels there.

---

## 2. The palette as CSS tokens

Sampled from the cafe's own room, not from a stock dark theme. The room is sand walls, a jute dune
canopy, rattan gourd lamps, olive green leather chairs on walnut frames, white ceramic cacti, a date
palm, travertine floor. The olive is the token that makes this site nobody else's.

The page runs a light arc, which is the premise made structural: the hero is dusk outside, the middle
sections are the lit interior in sand, and the page deepens to 2am at the bottom.

Sampled directly out of the approved hero frame with ffmpeg, so page and footage are literally the
same colours. Raw samples from the frame: sky at the top `#1B2D4E`, sky at mid height `#393E5A`,
shadowed sand trough `#282634`, lit sand `#322D3C`, the afterglow band `#E98B63`, the crest rim
`#81584F`, the glow beyond the ridge `#B87350`.

```css
:root{
  --canvas:#171723;          /* the frame's shadowed sand, darkened. never pure black */
  --canvas-deep:#0E0E16;     /* 2am. the booking band and the footer */
  --dusk-blue:#1B2D4E;       /* the frame's upper sky. the fixed background layer */
  --sand:#E8DECB;            /* the lit interior. menu and room sections */
  --sand-deep:#D9CBB2;       /* travertine. raised surfaces on sand */
  --panel:#1F1F2E;           /* cards on the dusk canvas */
  --olive:#4C5B3C;           /* the chairs. the brand's quiet signature colour */
  --olive-light:#8C9A6E;     /* olive legible on dusk */
  --walnut:#6B4A2F;
  --amber:#D9935F;           /* the glow beyond the ridge. glows and particles only */
  --accent:#E4794A;          /* the ember, straight off the afterglow band. CTA and rare emphasis */
  --accent-hover:#C85F33;
  --accent-muted:rgba(228,121,74,.22);
  --ember-deep:#B4451F;      /* the accent, legible as text on sand */
  --text-primary:#F4EDE1;    /* bone on dusk */
  --text-secondary:#9A94A8;  /* the frame's haze violet, on dusk */
  --ink:#211B16;             /* on sand */
  --ink-secondary:#5B5042;   /* on sand */
}
```

Measured contrast, computed not guessed:
`--text-primary` on `--canvas` 15.25:1 · `--text-secondary` on `--canvas` 6.07:1 ·
`--accent` on `--canvas` 6.03:1 · `--olive-light` on `--canvas` 5.88:1 ·
`--ink` on `--sand` 12.76:1 · `--ink-secondary` on `--sand` 5.89:1 ·
`--ember-deep` on `--sand` 4.13:1 (large text and borders only; body on sand uses `--ink`) ·
`--ink` on `--accent` button fill 5.78:1.

The accent appears on the call to action, focus rings, and two moments of emphasis. Nowhere else.

---

## 3. The type trio

- **Display: Syne**, weights 700 and 800. Warm geometric with unusual widths and real character.
  Not a Didone serif, which is the default every dark cinematic site reaches for.
- **Body: Hanken Grotesk**, weights 400, 500, 600. Quiet and warm.
- **Mono: Space Mono**, weights 400 and 700. The clock readout, the hour labels, the small HUD lines.
  It reads as a late shift, which is the point.

Subset to those weights only, with preconnect.

---

## 4. The band map

**Tier 2, two chained segments, about 12 seconds of footage.** Segment one descends the dune while the
sun finishes setting. Segment two picks up on segment one's exact final frame, the last daylight goes,
and the camera arrives at After Dunes among the palms. The seam lands inside motion and inside a light
change, which is what hides it (the seam law in `prompt-laws.md`).

**The premise is performed by the scroll itself: scrolling down is the sun going down, and the bottom
of the hero is arriving after it.**

Hero height **800vh**, so the scroll range is 700vh. Five beats. Ramps are computed from a target of
18vh rather than the default 0.02 cap: `f = Math.min((b - a) / 3, 18 / scrollRangeVh)`. Deviation
stated out loud. Plateau lands at about 83vh per beat. Validated by the flick test before anyone sees
the page.

**Composition:** the dune runs diagonally out of the lower left, the oasis sits right of centre on the
horizon line, and the sky fills the upper half. The action lane is the lower right. All copy lives
upper left to upper centre, clear of the sun and clear of the lamps.

| Band | Range (starting point) | Footage moment | Copy (verbatim) | Entrance |
|---|---|---|---|---|
| 1 | 0.00 to 0.17 | high on the dune, sun on the horizon raking the ripples warm, oasis lamps small and far | kicker `ALKAPURI · VADODARA` / headline `After Dunes` / sub `A cafe for the hours after.` | Drift-down. Words start above their resting spot and fall into place, echoing the sun sliding down. One-time load ramp on this band only, then scroll-driven. |
| 2 | 0.21 to 0.38 | descending the dune face, the sun sinking, sand streaming off the ripples | `The sun quits at seven.` / `We pour until two.` | Approach-from-depth on line one. Word-punch with overshoot on **two**. |
| 3 | 0.42 to 0.59 | the sun down to a sliver and then gone, the sky deepening, the lamps growing relatively brighter | `The light goes.` / `Ours comes on.` | Blur-to-sharp on line one as the daylight blurs out, then the second line punches in as the lamps take over. The two lines cross over exactly as the footage does. |
| 4 | 0.63 to 0.80 | the sand running out, the oasis close, lamp pools defined on the sand | `Past the last dune,` / `the lamps are still on.` | Scatter. Characters fly in from seeded random offsets, echoing the streaming grains. |
| 5 | 0.84 to 1.00 | arrived and at rest in front of After Dunes, jute canopy and gourd lamps lit | headline `Come after.` / sub `Open 8am to 2am, every day. Alembic Gorwa Road, Vadodara.` / buttons `Book a table` and `Call the cafe` | Word-by-word rise into a staged settle. Headline words rise in reading order, then the subline, then the button row. Three arrivals, one band. |

Band 1 skips the opacity ease-in. Band 5 skips the ease-out. Nothing snaps.

Every band carries all four legibility layers: the global radial scrim, a per-band scrim riding `--k`,
the three-layer text shadow token, and chips behind the small mono lines. Peak band alphas start at
0.62 for the quiet beats and 0.72 for band 2, tuned against each band's worst frame, audited to 3.5:1
worst-pixel contrast or better.

---

## 5. The static-hero copy block

What phones and reduced-motion visitors see, composed over the ending frame. A designed layout, not an
apology.

- kicker: `ALKAPURI · VADODARA`
- headline: `Come after.`
- sub: `After Dunes pours from 8 in the morning until 2 at night. Every day.`
- buttons: `Book a table` / `Call the cafe`

---

## 6. The below-fold outline

Every section funnels to the `#book` anchor. No two adjacent sections share a layout skeleton.

### 6.1 The hours — dusk canvas

- kicker: `WHY AFTER`
- headline: `Most cafes in Alkapuri are stacking chairs by eleven.`
- body: `We open at eight in the morning and we pour until two at night, seven days a week. The late hours are not an afterthought. They are the whole reason for the name.`
- Three tiles, read off the real listing: `4.5 Ambience` · `4.5 Service` · `211 ratings`
- Living element: the tile numbers count up once on entry, then rest.

### 6.2 The hour dial — dusk canvas — THE SIGNATURE AND THE INTERACTIVE MOMENT

A wide hand-drawn SVG arc running 8am to 2am, with the hours marked in Space Mono. A marker sits at the
visitor's actual current time in Vadodara, read live from their clock and converted to IST. The stretch
from sunset to 2am is lit in ember; the rest of the arc is a hairline.

- kicker: `THE DIAL`
- headline: `Hold it, and run the day down.`
- body: `Most of what makes this place worth the drive happens in the lit part of the arc. Press and hold.`
- live readout, computed, Space Mono, example shape: `IT IS 11:42 PM IN VADODARA · OPEN FOR 2 MORE HOURS`
  Closed state: `IT IS 4:10 AM IN VADODARA · WE OPEN IN 3 HOURS 50 MINUTES`
- The hold: pressing and holding runs the marker down the arc. The section's light goes from day to
  dusk to night as it travels. Releasing early eases it back, never snaps. Completing it lights up
  three cards in sequence:
  - `After work · 6pm` — `The room is at its best when the lamps beat the daylight. Order a cold coffee and take the corner seat under the palm.`
  - `After dinner · 10pm` — `Dessert and a long sit. Nobody will rush you and nobody will ask you to settle up.`
  - `After everything · 1am` — `The quiet hour. Half the room is working, the other half is talking. Last pour is two.`
- Reduced motion gets the completed state immediately, no hold required.

### 6.3 What you get — sand canvas — THE OBJECTION SECTION

The reviews ask for pictures and prices. This is the answer, and it is the reason this site beats a
listing page. Prices are the cafe's own, from their menu.

- kicker: `THE MENU`
- headline: `Pictures. Prices. No surprises at the table.`
- body: `The thing people ask us for most is a menu that shows what arrives and what it costs. Here it is. Everything on it is vegetarian.`

**Lead block, Dunes Specialties.** Four cards, set apart and given the most room, because this is the
part of the menu nobody else in Alkapuri has. The intro line:
`Four coffees you will not find down the road. This is the part of the menu the name is about.`

| Item | Price | Description (verbatim from the menu) |
|---|---|---|
| Arabic Qahwa | ₹255 | Traditional Emirati coffee brewed with cardamom and saffron, served with dates |
| Date Latte | ₹240 | Espresso blended with date syrup and steamed milk |
| Saffron Spanish Latte | ₹255 | Espresso, condensed milk and saffron |
| Pistachio Rose Latte | ₹250 | Creamy pistachio mix with rose essence |

**Then the plates**, with the two real photographs on the first two cards:

| Item | Price | Description | Photo |
|---|---|---|---|
| Penne Crème Pesto | ₹260 | Penne in a creamy pesto sauce | `dish-pesto.jpg` |
| Creamy Alfredo | ₹280 | Penne in a rich white sauce | `dish-alfredo.jpg` |
| Saffron Risotto | ₹316 | A creamy Italian rice dish with saffron | none |
| Mezze Platter | ₹275 | A spread of small Middle Eastern dishes | none |
| Bombay Club Sandwich | ₹195 | A triple decker vegetable sandwich | none |
| Karak Chai Toast | ₹230 | Toasted bread filled with cream cheese, soaked in strong spiced karak chai | none |

**Then the cold things**, a compact row:

| Item | Price | Description |
|---|---|---|
| Vanilla Sand Iced Latte | ₹255 | Iced espresso with vanilla and salted caramel |
| Saigon Cold Brew | ₹250 | Cold brew sweetened with Vietnamese condensed milk |
| Rose Gold Iced Latte | ₹255 | Espresso, rose syrup and cardamom milk, topped with gold dust |
| Affogato | ₹230 | A scoop of ice cream drowned in a shot of espresso |

- Section footnote: `About ₹1,200 for two on a normal visit. The full menu, all eleven sections of it, is on District.`

### 6.4 The room — sand canvas

- kicker: `THE ROOM`
- headline: `The most photographed room on Alembic Gorwa Road.`
- body: `A jute canopy waves across the ceiling like a dune. Rattan lamps, olive leather, white ceramic cacti, a date palm standing in the middle of it. People come in for a coffee and leave with a camera roll. We are glad about that.`
- Gallery of the real interior photographs, staggered, not a grid of equal squares.

### 6.5 What people say — dusk canvas

Real quotes, verbatim, with the sub-ratings beside them. A balanced one stays in, because a wall of
five stars reads as fake.

- kicker: `211 RATINGS`
- headline: `In their words.`
- `"Such a nice place and also the staff is very friendly."`
- `"Great ambiance, food taste and quality top notch and amazing service by staff."`
- `"Ambiance is well made, would stay for how well it themed."`
- `"The beverages were all good."`
- Footnote: `Ambience 4.5 · Service 4.5 · Food 4.2, from 211 ratings on District.`

### 6.6 Questions — dusk canvas

Answering the objections the research actually turned up.

- `Are you really open until 2am?` — `Every day. Eight in the morning to a quarter to midnight, then midnight to two. The kitchen slows down late but the counter does not.`
- `What should I order?` — `Start with the Dunes Specialties. The Arabic Qahwa is brewed with cardamom and saffron and comes with dates, and the Date Latte is the one people order twice. The plates are Continental and built for a long sit rather than a quick one.`
- `Is everything vegetarian?` — `Yes. There is no meat anywhere on the menu.`
- `How much is it for two?` — `About ₹1,200 for two on a normal visit. Pre-booked tables carry a discount through District.`
- `Can I come on my own and work?` — `Yes, and plenty of people do, mostly after nine. There are power points along the banquette wall.`
- `Do I need to book?` — `Not on a weekday. Friday and Saturday after eight, yes. Booking also gets you the table you actually want rather than the one that is free.`
- `Where exactly are you?` — `FF-105 and 106, Neptune Trion, Alembic Gorwa Road, Alkapuri, Vadodara.`

### 6.7 The light is on — deepest night canvas — THE CALL TO ACTION

- kicker: `BOOK A TABLE`
- headline: `The light is on.`
- body: `Tell us when and how many. The button opens WhatsApp with the message already written, so it takes one tap.`
- body: `Two ways in, and both of them are real. Ring the counter, or hold a table on District.`
- Primary button: `Call +91 97268 64562` → `tel:+919726864562`
- Secondary button: `Book a table on District` → the cafe's District listing
- Third link: `Get directions` → the Google Maps pin
- **Form handling on a static site: there is no form.** This is the "no form at all" option from
  Phase 8 of the skill, chosen deliberately. The cafe already takes bookings by phone and through
  District, so a form with no backend behind it would either fake a success state or quietly lose
  someone's booking. Two real destinations beat one pretend one.

### 6.8 Footer — deepest night canvas

Address, hours in full, phone, District and directions links, and a line of credit. The business is
real, so there is no fictional-brand disclosure. The footer does carry one honest line: the dune
imagery in the hero is generated, the photographs of the room and the plates are the cafe's own.

---

## 7. The vector layer plan

All of it hand drawn, all of it honoring reduced motion by showing final states and stopping drives.

- **The ridge lines.** Three hand-drawn SVG dune ridge curves that draw themselves along their path as
  each section enters. One per sand section, one across the hours section. They are the page's spine
  and they echo the jute canopy in the real room.
- **The hour arc.** The signature. Hand-drawn path, hour ticks in mono, an ember-lit segment from
  sunset to 2am, and a marker that the hold moves.
- **Sand grain.** A whisper-level particle field on the fixed background layer, drifting at about one
  pixel a second, cycling over 90 seconds. Paused off-screen and on hidden tabs.
- **The fixed environment layer.** One background behind everything: a very slow warm glow drift in the
  footage's grade plus the grain, so scrolling feels like moving through one place rather than past
  stacked sections.
- **Section motifs.** A small ceramic-cactus glyph and a gourd-lamp glyph, drawn as SVG, used as
  section markers at whisper weight.

---

## 8. The engineering list

The full standard, named so the build cannot half-remember it:

- Video fetched as a Blob so seeking works on hosts without Range support. Streamed with the honest
  progress ring if it lands over 8MB; plain blob fetch if under.
- Poster set from JavaScript inside the gated path, so phones never download either file.
- dt-normalized lerp in a rAF loop that rests when converged and when the hero is off-screen.
- Gated seeks, coalesced to the newest target, with the error handler that breaks the deadlock.
- Delta-gated DOM writes everywhere. `--k` gated at 0.008. Mono readouts throttled to 10Hz and written
  only when the string changes.
- Band pacing in scroll distance, validated by the flick test at 120, 240 and 360px steps.
- The four-layer legibility system, audited to 3.5:1 worst-pixel contrast per band.
- The five static-hero gates, identical strings in CSS and JS, armed and disarmed from change listeners
  on all five queries.
- Complete and beautiful without the video.
- Reduced motion honored completely and live, in both directions.
- `overflow-x: clip` on html and body with `hidden` declared first.
- Semantic landmarks, skip link, real heading hierarchy, `aria-hidden` on decorations, the video out of
  the tab order, `:focus-visible` in the accent, 44px touch targets under coarse pointer.
- Real title, meta description, theme-color, inline SVG favicon of the brand mark, and the
  `<!-- DEPLOY STEP -->` comment for the og tags.
- One living element per section at whisper level, negative animation delays, paused off-screen and on
  hidden tabs via the body-class pattern that reaches pseudo-elements.

---

## 9. The copy gate

Every viewer-facing line above ships verbatim. The built page must pass the Phase 9 grep gate before
anyone sees it: zero em dashes, zero instances of leverage, seamless, empower, unlock, robust,
actionable, data-driven and solutions, plus the body-copy sweep for AI tells across the whole file and
not just the hero.

Deliberate brand devices written here are craft and stay: the three-beat `After work · After dinner ·
After everything`, and the staccato `Pictures. Portions. No surprises at the table.` Both were chosen
on purpose for this brand.
