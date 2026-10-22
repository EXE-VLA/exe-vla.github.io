# EXE — project page

Project page for **EXE: Egocentric Cross-Embodiment Pretraining via Factorized Latent Actions
for VLA Models**.

- Live site (after publishing): `https://exe-vla.github.io/`
- Main project repo: `https://github.com/EXE-VLA/EXE`

Private while the paper is under review.

## Layout

```
index.html                     the page (editorial / research-blog style)
static/css/index.css           its stylesheet
academic.html                  alternative design, conventional academic project page
static/css/academic.css        its stylesheet
static/images/*.jpg            web-sized figures (displayed inline)
static/images/*.png            full-resolution figures (opened on click)
static/images/*_raw.png        gitignored intermediate renders
robots.txt                     crawler block while under review
.nojekyll                      serve files verbatim, skip Jekyll
```

`academic.html` is kept as a fallback design and is not linked from anywhere. Delete it if it is
no longer wanted.

## Design notes

Monospace body text with serif headings on a warm paper background, a 768 px prose column, and
wider dot-pattern panels for figures and charts.

Bar charts are plain HTML and CSS — no charting library. Bar heights are explicit pixel values
rather than percentages, so they never depend on percentage-height resolution inside a stretched
flex container (which silently collapses in some engines).

No third-party resources at all: no CDN, no web fonts, no analytics. The page renders identically
offline, on a local server, and on GitHub Pages.

Figures are rendered from `figure/*.pdf` of the LaTeX source with Ghostscript (`-r400` for the
diagrams, `-r300` for the photo panels), then downscaled to 2200–2400 px wide.

## Local preview

No build step and no dependencies:

```bash
python3 -m http.server 8000
# http://localhost:8000/                 the page
# http://localhost:8000/academic.html    alternative design
```

## Going public

1. Delete `robots.txt` and remove the `<meta name="robots" content="noindex, nofollow">` tag
   from `index.html`.
2. Replace `Anonymous Authors` in the meta block, the footer, and the BibTeX entry with the real
   author list and affiliations.
3. Fill in the arXiv and code links, currently rendered as struck-through placeholders in the
   masthead.
4. Flip the repository to Public, then enable Pages:
   **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.
