# Ryan's personal site — handoff for the coding agent

A four-page static personal website. The design is final. It came from a design canvas
(the "Statement" direction), and these files are a faithful HTML/CSS build of it. Your job is
to take it from here: fill in content, harden it, and deploy. Don't redesign it.

## What's here

```
index.html          Home: name, short intro, links to Present · Harvard · Past
present/index.html  What Ryan is doing now (Topos)
harvard/index.html  Time at Harvard
past/index.html     Earlier chapters: links to one subpage each
past/powerlifting/  Best lifts and the world-record video
past/photography/   Albums (Home, Iceland, Misc), each a small arrow-key slideshow;
                    photos in past/photography/<album>/NN.webp, white mats trimmed
blog/index.html     Blog index (empty for now)
style.css           All styles (one file, no framework)
fonts/              CMU Serif (Computer Modern), roman + italic, Latin subset, SIL OFL
```

No build step. The only JavaScript is the slideshow script inline on the photography page
(progressive enhancement: without it the photos still swipe and scroll). Pages use root-relative paths (`/style.css`, `/present/`),
so serve the folder from a web root: `python3 -m http.server` from this directory, then open
http://localhost:8000. Opening the files directly with `file://` breaks the paths.

## Design rules (keep these)

- **Typeface:** CMU Serif only. Roman and italic, one weight (400). No bold anywhere.
  Hierarchy comes from small caps and size. Italics are for quotations and book titles only
  (Ryan's rule; titles use `<cite>`): no italic headings, notes, dates or nav states.
- **Colour:** two tokens only: `--bg #faf9f5` (warm paper) and `--fg #161616`.
  Light only, no dark mode (Ryan's preference); don't add a `prefers-color-scheme` switch.
  No accent colour, borders, shadows or icons. Images only on the photography page.
- **Home:** everything centred in a 540px column: a small italic epigraph (the Perelman
  quote, no attribution), then the name in small caps at 30px (larger than the intro, by
  Ryan's request), then the intro, then the section links separated by middots. Contacts sit
  in a footer pinned to the bottom of the screen: both emails, LinkedIn and X, separated
  by `/`, and splitting into two lines on phones.
- **Inner pages:** a 560px column. The small-caps name at the top is centred and links home.
  Then a centred `h1`, then left-aligned body text. Footer nav repeats
  Present · Harvard · Past · Blog, with the current page at 60% opacity (`aria-current="page"`, not a link).
- **Links:** no underline by default, and a 0.5px underline on hover. Links inside body
  lists use `.u`, which keeps them always underlined.
- **Sizes:** body 19px / 1.65 (home 21px / 1.6). Inner `h1` 30px. List notes 17px.
- **Photos:** understated, never full-bleed. They stay inside the 560px column at 340px tall
  (280px on phones), with ← n / N → controls under them (Ryan wants it nonchalant).
- Must work at phone width (390px). Timeline rows stack below 480px.

## To do

1. **Content.** Everything in `[brackets]` is a placeholder: surname, intro, the meta
   description, and each page's paragraph and entries. Ask Ryan for the real text and
   don't invent biographical facts. Add or remove `<li>` entries freely; the layout handles any count.
2. **Metadata.** Add a favicon (a simple monogram, or none), Open Graph/Twitter tags with the
   title and description, and a canonical URL once the domain is known.
3. **Deploy.** Any static host works (GitHub Pages, Cloudflare Pages, Netlify, Vercel).
   Ask Ryan which host and domain he wants. Add a 404 page in the same style
   (centred name, a "Not found" heading, a link home).
4. **Optional, only if asked:** a generator such as Eleventy or Astro, so entries can live in
   Markdown or data files. Output must stay identical, with no client-side JavaScript beyond the slideshow.

## Checks before shipping

- Lighthouse: Accessibility 100, no layout shift (fonts are preloaded with `font-display: swap`).
- Text contrast is at least 4.5:1 (it is now; keep it if you add grey text).
- Every page is checked at 390px, 768px and 1440px.
