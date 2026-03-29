# Listen Vinyl — Publishing Rhythm

## The Target

One article per week. Published on Sundays. No exceptions, no gaps — the schedule should be treated as a commitment, not a suggestion.

---

## How to Add an Article

1. Create a new markdown file in `src/posts/` with a URL-friendly filename.
   Example: `src/posts/best-ambient-albums-vinyl.md`

2. Add the frontmatter at the top of the file:

   ```
   ---
   layout: layouts/article.njk
   title: "..."
   description: "..."
   category: "Gear" (or Listening Guides, Discovery, Best Albums)
   tag_class: "tag--teal" (Gear) / "tag--amber" (Listening Guides, Best Albums) / "tag--muted" (Discovery)
   read_time: "X min read"
   date: YYYY-MM-DD
   featured: false
   ref: "LV-XXX"
   toc_1: "Section One Heading"
   toc_2: "Section Two Heading"
   toc_3: "Section Three Heading"
   toc_4: "Section Four Heading"
   toc_5: "Section Five Heading"
   tags:
     - Tag One
     - Tag Two
   ---
   ```

3. Write the article body in markdown below the frontmatter.
   Target: 1500–2500 words. Confident editorial voice. Specific. Opinionated. No padding.

4. Increment the ref number from the last published article.
   Current sequence: LV-001 (Kind of Blue) through LV-007 (Nick Cave Discovery).
   Next article: LV-008.

5. Commit and push:

   ```bash
   cd ~/Sites/listenvinyl-eleventy
   git add src/posts/your-new-article.md
   git commit -m "Add article: Your Article Title [LV-XXX]"
   git push
   ```

6. Netlify auto-deploys on push to main. Check https://listenvinyl.com after a few minutes.

---

## Content Schedule

The next 12 weeks of planned articles are in:
`CONTENT_SCHEDULE.md`

Keyword targets and research are in:
`keywords.md`

---

## Article Quality Standards

- Lead with a dropcap paragraph wrapped in `<p class="dropcap">...</p>`
- Use pullquotes (`<div class="pullquote">`) for 1–2 memorable lines per article
- Use infoboxes (`<div class="infobox">`) for practical tips, buying recommendations, or asides
- End each article with a concrete recommendation or clear next step for the reader
- No listicle filler. Every paragraph should say something specific.
- Voice: editorial authority, not hedged. "This pressing is worth the money" not "some people think this pressing might be worth considering."

---

## Category Tags

| Category | tag_class | Colour |
|----------|-----------|--------|
| Gear | tag--teal | Teal |
| Listening Guides | tag--amber | Amber |
| Best Albums | tag--amber | Amber |
| Discovery | tag--muted | Muted grey |

---

## Scheduling Notes

- If a week is missed, do not publish two articles the following week. Maintain the one-per-week rhythm; just shift the schedule.
- Featured articles (featured: true) appear prominently on the homepage. Use sparingly — one per month maximum.
- The Kind of Blue article (LV-001) is the current featured article. Update this when a new article warrants it.
