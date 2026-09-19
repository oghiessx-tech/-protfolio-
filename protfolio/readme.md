# Abdullah Khan — Developer Portfolio

A premium, single-file, dark-themed developer portfolio with a Three.js hero
scene, a draggable 3D skills ring, scroll reveals, and a fully responsive
layout. No build step, no framework, no dependencies to install — it's one
HTML file that pulls fonts and Three.js from a CDN at runtime.

## 1. Preview it locally

You can just double-click `index.html` and it will open in your browser.
For the best experience (and to avoid any browser quirks with local files),
serve it instead:

```bash
# Python 3
python3 -m http.server 8080
# then open http://localhost:8080

# or, if you have Node:
npx serve .
```

## 2. Deploy it (pick one)

**Netlify (easiest)**
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the whole project folder onto the page
3. You get a live URL immediately — add a custom domain later if you want one

**Vercel**
1. `npm i -g vercel` (one-time)
2. Run `vercel` inside this folder and follow the prompts

**GitHub Pages**
1. Push this folder to a GitHub repo
2. Repo → Settings → Pages → set the source branch to `main` and folder to `/`
3. Your site will be live at `https://yourusername.github.io/repo-name`

Any of these gives you a URL you can paste straight into your Fiverr profile.

## 3. Before you publish — edit these placeholders

The brief asked me not to invent fake stats, fake testimonials, or fake
links, so a few things are intentionally left as clearly-marked placeholders.
Search the file for `EDIT:` comments to find each spot, or use this list:

| What | Where | Search for |
|---|---|---|
| Real domain / OG image | `<head>` | `yourdomain.com`, `og-image.jpg` |
| Email, GitHub, LinkedIn, Fiverr URLs | Contact section + Footer | `your.email@example.com`, `yourusername` |
| About-section stats | `about` section | `data-target="0"` (4 stats — one, "Technologies," is pre-filled at 10 since that's just a count of the skills listed below it) |
| Project titles, descriptions, tech tags, links | `projects` section | `<!-- EDIT: replace each project's -->` |
| Project screenshots | `projects` section | Each `.project__screen` div — replace it with `<img src="your-screenshot.jpg" alt="...">` |
| Testimonials | bottom of the main script, `TESTIMONIALS` array | `TESTIMONIALS = [` |
| Contact form backend | `#contactForm` | Currently validates in the browser only and shows a mock success message — wire it to [Formspree](https://formspree.io) or [EmailJS](https://www.emailjs.com/) (both have a free tier and a few lines of setup), or point the `<form>` at your own backend endpoint |

Nothing above will look broken if you forget to edit it — the placeholders
are written so they read sensibly on their own — but the site will convert
better once they reflect your real numbers, work, and links.

## 4. Customizing the design

Everything themeable lives in one place: the `:root` block at the top of
the `<style>` tag (search for `0. TOKENS`). Change `--blue`, `--violet`,
`--teal` to re-theme the whole site, or swap the two font families loaded
in the `<head>` (currently Clash Display for headings, General Sans for
body text, JetBrains Mono for the small code-style tags).

The file is organized with numbered comment headers (`1. RESET & BASE`,
`6. HERO`, `9. SKILLS`, etc.) in both the CSS and the section markup, so you
can jump to the part you want with your editor's search.

## 5. What's already handled

- Fully responsive (tested breakpoints at ~980px and ~640px)
- `prefers-reduced-motion` respected — the 3D scene, cursor, and reveal
  animations all degrade gracefully for people who've asked for less motion
- Keyboard-visible focus states, a skip-to-content link, and semantic
  landmarks (`header` / `main` / `section` / `footer`)
- No external icon font or logo assets — icons are a hand-drawn inline SVG
  sprite, so there's nothing to fetch and nothing to go missing
- The Three.js hero scene pauses when the tab isn't visible and scales its
  particle count down on small screens to keep things smooth on mobile
- No console errors and no dead links — every internal link points to a
  real section; the only `href="#"` placeholders are the project demo/GitHub
  buttons, which are meant to be filled in per project (see the table above)

## 6. File structure

```
index.html   → the entire site (structure, styles, and scripts in one file)
README.md    → this file
assets/      → empty on purpose — drop real project screenshots here and
               point the <img> tags at them (see step 3)
```

Everything is inline on purpose: it makes the site trivially portable —
one file, drag-and-drop deploy, nothing to bundle.