# Perri Brothers Construction

Static marketing site for Perri Brothers Construction, a family-owned renovation and
construction company serving Lee and Collier counties in Southwest Florida.

No build step, no dependencies. Plain HTML, CSS and JavaScript.

---

## Contents

```
index.html            all six pages (hash router, no page reloads)
404.html              bounces unknown paths back to /
css/styles.css        all styles
js/main.js            asset paths, page router, and every interactive component
images/               31 optimised WebP / PNG assets
CNAME                 custom domain for GitHub Pages
robots.txt            crawler rules
sitemap.xml           sitemap
.nojekyll             stops GitHub Pages running Jekyll over the files
```

## Pages

Home, About, Services, Process, Reviews, Contact. They are all in `index.html` and
switch client side via the URL hash (`/#/about`, `/#/services`, and so on), so the
whole site loads once and navigation is instant.

## Deploying

### GitHub Pages
1. Create a repository and push these files to the default branch.
2. Settings, then Pages, then set Source to *Deploy from a branch* and pick the branch
   with `/ (root)` as the folder.
3. For the custom domain, keep `CNAME` in place and point DNS at GitHub:
   - `A` records for `perribrothers.com` to `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153`
   - `CNAME` record for `www` to `<username>.github.io`
4. Tick *Enforce HTTPS* once the certificate is issued.

If you are not using a custom domain, delete `CNAME`. The site will live at
`https://<username>.github.io/<repo>/`. In that case the absolute URLs in the
`<head>` of `index.html` (canonical, Open Graph, structured data) and in
`sitemap.xml` and `robots.txt` should be updated to match.

### Netlify or Vercel
Drag the folder into Netlify, or import the repo in Vercel. There is no build
command and the publish directory is the repository root.

---

## Before it goes live

These need real information from the client:

1. **Contact form.** Wired to LeadConnector (HighLevel) as an iframe embed on the Contact
   page, form id `8VDXtzsYXkVH5dgba4f7`, "Perri Website Form". Submissions go straight
   into the CRM. The iframe is cross-origin, so **nothing inside it can be styled or
   reworded from this repository** — field labels, placeholder text, the submit button,
   validation messages and the thank-you screen are all edited in the LeadConnector form
   builder. `js/form_embed.js` from `link.msgsndr.com` resizes the iframe to fit.
2. **Licence number.** Florida contractors normally display this. There is no
   placeholder in the markup, so add it to the footer once supplied.
3. **Review attribution.** The "Recent work" strip on the Reviews page is
   deliberately not tied to any named reviewer, because we cannot claim a given
   photo belongs to a given client. Once the client confirms which project matches
   which review, the photos can be paired to the reviews.
4. **Vector logo.** The wordmark and monogram were traced from a raster file. An SVG,
   AI or EPS original would render more crisply at large sizes.


## Checking mobile and tablet without a phone

The site is responsive, so there is no separate mobile file. To preview it at real device
sizes there is a hidden tester: a gold circle in the bottom right corner. Tap it and pick
Mobile, Tablet or Desktop, then choose a specific device from the dropdown (iPhone SE
through iPhone 15 Pro Max, iPad mini through iPad Pro 12.9, Pixel, Galaxy, and laptop and
desktop widths). Rotate gives you landscape. Close returns you to the site.

It appears automatically in three situations:

1. **Working locally.** Open `index.html` from your computer, or run a local server, and
   the circle is there with nothing to configure.
2. **On the live site with a flag.** Visit `https://perribrothers.com/?preview`.
3. **Shift + D** on any page turns it on, in case the url gets rewritten.

Once switched on it stays on for the rest of that browser tab.

Ordinary visitors never see it. On a public url without the flag, the control is removed
from the page entirely.

## Editing content

Most copy is plain HTML in `index.html`. Three things live in `js/main.js` as data
arrays so they only have to be edited in one place:

- `SVC` — the five services, their scope lists and their images
- `REV` — the client reviews
- `BA` — the before and after projects in the homepage slider

### The `SVC` fields

The home page and the Services page deliberately describe each service differently, so
every entry carries three separate pieces of prose. Editing one does not change the others:

| field    | where it appears                                        |
| -------- | ------------------------------------------------------- |
| `t`      | title, used in both places                              |
| `card`   | short description on the home page service cards        |
| `teaser` | one-line description in the Services page accordion header |
| `p`      | main paragraph inside the open accordion panel          |
| `tags`   | chips on the home card, and the uppercase row under the accordion title |
| `s`      | the scope list inside the panel                         |
| `f`      | the "Right call if" line                                |

The header `teaser` fades out when its panel opens, so a visitor never reads the teaser
and the paragraph at the same time.

## The black band on the home page

The dark "Built for Southwest Florida" section carries a faint photographic texture: the
finished tongue-and-groove foyer ceiling at 8% opacity, desaturated and faded out top and
bottom. It is set in `css/styles.css` on `.coast::before`, not in the markup, so swapping
it is a one-line change. Keep the opacity in the 5–10% range; above that it starts to
fight the headline.

## Images

All images are pre-optimised WebP, except the logos which are PNG with transparency.
Everything below the hero is lazy loaded. If you replace an image, keep the same
aspect ratio, or adjust the matching `aspect-ratio` rule in `css/styles.css`.

## Browser support

Modern evergreen browsers. Uses CSS grid, `clamp()`, `aspect-ratio` and
`overflow: clip`. Motion is disabled automatically for anyone who has
`prefers-reduced-motion` set.
