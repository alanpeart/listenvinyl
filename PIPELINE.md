# Listen Vinyl — Publishing Pipeline

## Live Site

URL: https://listenvinyl-pub.netlify.app
GitHub: https://github.com/alanpeart/listenvinyl
Netlify Site ID: 20f18d49-fef8-41cf-be98-0d2313a83b7c

---

## How to Add a New Article

1. Create a new Markdown file in `src/posts/`:

   src/posts/your-article-slug.md

2. Add frontmatter at the top:

```yaml
---
layout: layouts/article.njk
title: "Your Article Title"
description: "A one-sentence description of the article."
category: "Listening Guides"     # or "Gear", "Discovery", "Best Albums"
tag_class: "tag--amber"          # tag--amber, tag--teal, or tag--muted
read_time: "10 min read"
date: 2026-04-01                 # YYYY-MM-DD
featured: false                  # set true for ONE post to appear as featured
ref: "LV-005"                    # sequential reference number
album_title: "Album Name"        # optional: sidebar album card
album_artist: "Artist Name"      # optional
album_label: "Label, Year"       # optional
album_pressing: "Original"       # optional
album_rating: "Essential"        # optional
toc_1: "Introduction"            # table of contents labels (up to 5)
toc_2: "Background"
toc_3: "Details"
toc_4: "Recommendations"
toc_5: "The Verdict"
tags:
  - Tag One
  - Tag Two
---
```

3. Write the article body in Markdown below the frontmatter.

   - Use `<p class="dropcap">` for the first paragraph to get the drop cap effect
   - Use `<div class="pullquote">` for pull quotes
   - Use `<div class="infobox">` for info boxes
   - Use `<div class="tracklist">` for track listings

4. Commit and push to GitHub — Netlify auto-builds.

---

## Frontmatter Fields Reference

| Field | Required | Description |
|-------|----------|-------------|
| layout | Yes | Always `layouts/article.njk` |
| title | Yes | Article headline |
| description | Yes | One-sentence summary (used in meta and card excerpts) |
| category | Yes | Content category (Listening Guides, Gear, Discovery, Best Albums) |
| tag_class | Yes | CSS class for tag colour: `tag--amber`, `tag--teal`, `tag--muted` |
| read_time | Yes | Estimated read time, e.g. "12 min read" |
| date | Yes | Publication date YYYY-MM-DD |
| featured | No | `true` to show as homepage featured article (one post only) |
| ref | No | Internal reference number, e.g. LV-005 |
| album_title | No | Shows sidebar album card |
| album_artist | No | Artist for sidebar card |
| album_label | No | Label and year |
| album_pressing | No | Best pressing recommendation |
| album_rating | No | Rating label (Essential, Highly Recommended, etc.) |
| toc_1 to toc_5 | No | Table of contents section labels |
| tags | No | Array of topic tags |

---

## How Deployment Works

### Automatic (recommended)
1. Write your article in `src/posts/`
2. `git add . && git commit -m "Add article: title" && git push`
3. Netlify detects the push, runs `npx @11ty/eleventy`, and deploys `_site/`
4. Site is live at https://listenvinyl-pub.netlify.app within ~30 seconds

### Manual (via zip deploy)
Run the deploy script to rebuild locally and push directly:

```bash
cd ~/Sites/listenvinyl-eleventy
npx @11ty/eleventy
python3 netlify_deploy.py
```

Note: manual deploy skips GitHub linking and overwrites the current deploy.

---

## Project Structure

```
listenvinyl-eleventy/
  .eleventy.js          — Eleventy config (input: src/, output: _site/)
  package.json          — npm dependencies
  netlify.toml          — Netlify build settings
  src/
    _includes/
      layouts/
        base.njk        — base HTML shell (head, nav, footer, scripts)
        home.njk        — homepage layout (all sections)
        article.njk     — article layout (hero, body, sidebar)
    _data/
      site.js           — global site metadata
    css/
      style.css         — main stylesheet (from prototype)
      article.css       — article-specific styles (from prototype)
      v2.css            — v2 design overrides (maximalist atomic age)
    articles/
      index.njk         — homepage (uses home.njk layout)
      about.njk         — about page
    posts/
      kind-of-blue.md
      best-turntables-under-200.md
      if-you-love-radiohead.md
      best-jazz-albums-vinyl.md
```

---

## TODOs and Known Issues

1. GitHub CI: The Netlify-GitHub link is set via API (repo: alanpeart/listenvinyl, branch: main). 
   Verify auto-builds are triggering at app.netlify.com > listenvinyl-pub > Build & Deploy.
   If auto-builds aren't running, you may need to install the Netlify GitHub App at:
   https://github.com/apps/netlify

2. Custom domain: The site is on listenvinyl-pub.netlify.app. To use listenvinyl.com,
   add the domain at app.netlify.com > listenvinyl-pub > Domain settings.

3. Featured post: Only one post should have `featured: true`. Currently kind-of-blue.md
   is featured. Change this by setting featured: false on it and featured: true on another.

4. Newsletter: The newsletter form submits to nothing (onsubmit="return false"). 
   Integrate with Mailchimp, ConvertKit, or Netlify Forms when ready.

5. Article pagination: No pagination yet. All posts are listed; add a posts index page 
   if the archive grows large.

6. Images: No real images yet — the design uses CSS-only vinyl illustrations and SVGs.
   To add a real image, place it in src/images/ and add a passthrough copy in .eleventy.js:
   eleventyConfig.addPassthroughCopy("src/images");
