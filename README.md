# VisionAI · editorial page

Public "who makes VisionAI" page (responsable editorial), linked from the VisionAI profiles on Instagram, TikTok and YouTube. It states who edits the channel, how to contact him, how the videos are made (AI voices labelled, AI-assisted scripts reviewed by a person, primary sources on screen) and that he sells Jarvis.

Live at: https://dpachonvare.github.io/visionai/ (GitHub Pages, branch `main`, folder `/`).

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The whole page: markup and CSS in one file, no JavaScript. |
| `assets/visionai-192.png` | Logo shown next to the name (the V from `marketing/marca` in the Jarvis repo). |
| `assets/visionai-512.png` | Image used in link previews (`og:image`). |
| `assets/apple-touch-icon.png`, `assets/favicon-32.png` | Browser and home-screen icons. |
| `assets/fonts/inter-400.woff2`, `inter-600.woff2` | Inter, Latin subset (covers á, é, í, ó, ú, ñ, ¿, ¡), from `@fontsource/inter` 5.3.0. |
| `assets/fonts/LICENSE-Inter.txt` | Inter's license (SIL Open Font License 1.1), which allows bundling the font. |

## How the code works

- **Static page, no scripts.** The page is plain HTML and CSS, so there is nothing to build and nothing that can break at runtime. GitHub Pages serves `index.html` as is.
- **Self-hosted font.** The two `@font-face` rules load Inter from `assets/fonts/` instead of Google Fonts. Visitors' browsers never contact a third party, which matters for viewers in the EU. `font-display: swap` shows the system font first if Inter is slow, and the `preload` link fetches the regular weight early.
- **Brand colours as CSS variables.** `:root` holds the navy gradient and the light halos from `marca.js`, the canvas code that draws the logo, so the page matches the profile picture. The body background stacks three `radial-gradient` halos (blue, teal, violet) over a diagonal `linear-gradient`, the same composition as the logo.
- **Layout.** A single centred column, 640 px max, with a 16 px side gutter so nothing scrolls sideways on a phone (checked at 390 px wide). Most visitors arrive from the in-app browsers of Instagram and TikTok, so it is designed for mobile first. One `@media (min-width: 600px)` rule adds space and a larger heading on bigger screens.
- **E-mail address.** The `mailto:` link and the visible address are written as HTML character references (`&#100;&#105;...`). Browsers decode them, so people see and click a normal address, but simple bots that scan page sources for `name@domain` patterns miss it. It slows spam down; it does not stop a determined scraper.
- **Accessibility.** `lang="es"`, real headings, an empty `alt` on the decorative logo (the brand name is right beside it), a labelled `<nav>` for the social links and a visible focus ring for keyboard users. Text contrast on the navy background is well above WCAG AA.
- **Link previews.** The `og:` meta tags give WhatsApp, iMessage and Instagram DMs a title, description and the logo when someone shares the link. `og:image` must be an absolute URL, so it points at the live site.

## Editing

1. Change the text inside `<article class="card">` in `index.html`.
2. Update the date in `<footer>`.
3. Commit and push to `main`. GitHub Pages republishes in about a minute.

The source text lives in the Jarvis repo, `MARKETING.md`, section 4, "Responsable editorial". Keep both in sync.
