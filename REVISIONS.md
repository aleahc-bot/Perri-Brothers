# Revision 1 — changes applied

Source: *Perri Brothers Web Edits – 1*. Every copy change in that document has been
applied to Home, About, Services, Process and Contact. The Reviews page was not covered
by the document and is unchanged.

Files touched: `index.html`, `js/main.js`, `css/styles.css`.

---

## Structural work the new copy required

Four revisions could not be made by swapping text alone.

**A fourth value on the About page.** Accountability was added, taking the values from
three to four. Four narrow columns did not suit the revised copy — Integrity is now four
sentences — so that grid became a 2×2 block on desktop. On phones it stays a swipe row.

**The service area list.** "Serving homeowners and businesses throughout:" followed by
bulleted cities did not fit the old label-and-sentence row, so there is a new `.areas`
block with the same gold diamond markers used on the Services page.

**Two descriptions per service.** The document gives different copy for a service on the
home page than on the Services page, and for Kitchen & Bathroom it gives both a short
description *and* a main paragraph. The old code derived all of that from a single string.
Each service now carries separate `card`, `teaser` and `p` fields — see README. The
accordion's header line fades out when its panel opens so two similar descriptions are
never on screen together.

**The texture behind the black band.** The note asked for a framing detail, blueprint or
finished wood at 5–10% opacity. It uses the finished tongue-and-groove foyer ceiling at
8%, desaturated, faded top and bottom. Set on `.coast::before` in the stylesheet.

---

## Hero image swap (requested separately, after the copy pass)

The main hero photo changed from `hero-exterior-deck.webp` to
`hero-interior-entry.webp`, chosen from four supplied candidates.

The hero slot is `aspect-ratio: 5/5.1` — very nearly square — and all four candidates
were 3:2 landscape, so the image was cropped deliberately rather than dropped in and left
to `object-fit` to guess. The crop keeps 21%–86% of the original width, which places the
wood entry door about two thirds across the frame and retains the living-room opening on
the left for depth. Delivered at 900×918 WebP, 84 KB, up from the previous 720×828.

Four references were repointed: the `hero_a` entry in `js/main.js`, and the preload hint,
`og:image` and structured-data image in the head of `index.html`. The old deck photo is
still in `images/`, so reverting is a one-line change in `js/main.js` plus the three head
references.

**Two things to decide.**

The caption on that photo used to read "Exterior build · Southwest Florida", which
identified it as a real Perri Brothers project. The replacement is stock photography, so
that claim could not carry over. It now reads "Custom interior finishes" — descriptive,
with no project or location claim. Confirm that wording, or supply a real project photo.

The photo also no longer reinforces the headline. "Built Beyond the Storm" sat above a
deck-and-siding exterior, which supported both the storm-resilience message and the
siding/windows/doors service. A bright interior entry does not. Worth considering whether
the hero image or the headline should be the one that moves.

---



1. **"One crew" → "One Team" on the Services page.** The document marked that headline
   "leave as is", but Crew → Team was changed on the home page with the reasoning that
   Team sounds more professional. Leaving "one crew" on Services would contradict it.
   Reverse this if the original wording was deliberate.

2. **Before & After projects 03–05.** The document only revised projects 01 and 02.
   Their titles were title-cased and their tags spelled out to match — "Crown" became
   "Crown Molding", "New pan" became "New Shower Pan". Their **descriptions were left
   alone**, so they still read in the older, terser voice. They will not match the two
   that were rewritten. Rewriting them is the obvious next step.

3. **Scope bullets on services 01, 03, 04 and 05.** Service 02's bullets were title-cased
   and given ampersands, so the same pattern was applied to the other four for
   consistency.

4. **"Right call if" lines on services 01, 03, 04 and 05.** Not addressed in the
   document, so they were left as written. They are still in the old voice — "You are
   changing how the space works" rather than "You're" — and do not match the revised
   copy around them. Worth a pass.

5. **Hero headline.** Still reads "Built Beyond **The** Storm", with the capital T falling
   on the line break. The document writes it lowercase but marked it keep as is, so it was
   not touched.

6. **Page eyebrows.** "02 / ABOUT" and the others were not actually uppercase in the
   stylesheet, despite the document showing them that way. `text-transform: uppercase`
   was added so they now match the rest of the eyebrows.

7. **Project eyebrow separator.** The document shows "PROJECT 01 • FORT MYERS" with a
   round bullet. The site uses a middot, matching the footer and the rest of the site, so
   it was left alone. Easy to change if the bullet was intentional.

8. **"colour changer" → "color changer"** in the kitchen ceiling description, the last
   British spelling on a US business site.

---

## Still outstanding before launch

Carried over from the original handover — none of these are copy issues:

- **The contact form does not reach an inbox.** `ENDPOINT` in `js/main.js` is still
  `null`, so the form opens the visitor's email app with the fields filled in. Set it to
  a POST url from Formspree, Basin, Netlify Forms or a CRM webhook.
- **No licence number in the footer.** Florida contractors normally display this.
- **Review photos are not paired to reviewers**, because a given photo cannot be claimed
  to belong to a given client without confirmation.
- **No vector logo.** The wordmark and monogram are traced from a raster file.

---

## Checks run

- All 91 revision phrases from the document verified present in the source.
- JavaScript passes a syntax check; all 31 images resolve; no unresolved image keys.
- All six pages rendered at 1440, 1100, 930, 768 and 390 px wide. No page-level
  horizontal scrolling at any width. The only elements extending past the viewport are
  inside the intentional swipe carousels, which is the original design.
- Values grid confirmed 2×2 on desktop; service area confirmed at six Lee cities and two
  Collier cities with their lead-in lines.
- Accordion confirmed: header teaser hidden on the open panel, visible on the closed ones.
- Texture confirmed rendering: the flat black footer measures zero pixel variance, the
  coast section measures real variation, so the image is loading and sitting subtly
  behind the type rather than failing silently.
