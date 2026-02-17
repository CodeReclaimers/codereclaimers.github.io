# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Static HTML/CSS website for CodeReclaimers, LLC, hosted on GitHub Pages. There is no build system, no JavaScript framework, and no templating engine — just plain HTML files served directly. The `_config.yml` exists for GitHub Pages/Jekyll but the site doesn't use Jekyll features (no layouts, no includes, no Liquid templates).

## There Are No Build Commands

No build, lint, or test commands. To preview locally, open any HTML file in a browser. Deployment happens automatically when changes are pushed to `main` — GitHub Pages serves the files as-is.

## Adding a Blog Post

This is the most common task and requires updating **three files**:

1. **Create the post** in `blog/` as a new `.html` file (kebab-case naming). Use an existing post as a template. Every post must include:
   - `<title>` with ` - CodeReclaimers` suffix
   - `<meta name="description">` with a one-sentence summary
   - `<link rel="canonical">` with the full absolute URL
   - Open Graph tags: `og:title`, `og:description`, `og:url`, `og:site_name` ("CodeReclaimers"), `og:type` ("article"), `article:published_time`
   - Twitter Card tags: `twitter:card` ("summary"), `twitter:title`, `twitter:description`
   - JSON-LD structured data block with `@type: "BlogPosting"`, author/publisher as "CodeReclaimers, LLC"
   - CSS link as `../css/style.css` (relative path up one level from blog/)
   - Google Fonts link for Open Sans and Source Sans Pro
   - Body structure: `.site-header` → `.content` (with `.back-link`, `h1`, `.date`, post content, `footer`)

2. **Update `index.html`** — add a new `<li>` to the `.blog-list` `<ul>`, inserted in reverse chronological order (newest first).

3. **Update `sitemap.xml`** — add a `<url>` entry with `<priority>0.8</priority>` and update the homepage `<lastmod>` date.

## Content Conventions

- Use HTML entities for typography: `&rsquo;` for curly apostrophes, `&ldquo;`/`&rdquo;` for curly quotes, `&mdash;` for em-dashes, `&rarr;` for arrows.
- Code examples in posts use `<pre><code>...</code></pre>` with HTML-encoded angle brackets (`&lt;`, `&gt;`).
- The site max content width is 750px (set in CSS). Blog posts don't need to worry about this — it's handled by the `.content` class.
