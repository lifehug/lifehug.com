# lifehug.com

Dave Taylor's personal site. Static HTML on GitHub Pages, served at https://lifehug.com from the
`main` branch of `lifehug/lifehug.com`. No build step: a push to `main` is live in about a minute.

This file is committed and publicly readable. Do not put private notes in it.

## Layout

| Path | What it is |
|---|---|
| `index.html` | Homepage. Inline CSS, one small inline script. |
| `book-of-mormon/index.html` | First long-form post (a "Musings" entry). |
| `assets/post.css` | Shared stylesheet for every long-form post. |
| `_template/index.html` | Starting point for a new post. Copy it; never link to it. |
| `CNAME`, `.nojekyll` | GitHub Pages settings. Leave alone. |

## Adding a new post

Always start from the template so the post gets the shared styling, the analytics tag and the
links back to the homepage without anyone having to remember them.

1. Copy `_template/` to `/<slug>/` (lower-case, hyphenated, e.g. `yield-inversion/`).
2. In `/<slug>/index.html` replace every `POST_*` placeholder (title, description, slug, date)
   and delete the `noindex` line and the `TEMPLATE:` comments.
3. Write the post inside `<main>`. Use the components in the template's comment block (tiles,
   note, figure, bar rows, tables). Style comes from `/assets/post.css`; add post-specific CSS
   in a `<style>` block in that post only if the shared file has nothing suitable.
4. Add `preview.png` (1200 x 630, a screenshot of the top of the post) to the post's folder.
5. Add the post to the homepage: in `index.html`, inside `<details id="musings">`, add an
   `<li id="<slug>">` at the top of the list (newest first), copying the existing entry, and
   raise the number in that section's `<span class="count">`.
6. The share link is `https://lifehug.com/#<slug>`: it opens Musings and highlights the entry.

## Rules for every page

- **Analytics:** every page must carry the Google tag snippet (`GTM-PW4VK99V`) in `<head>`,
  exactly as it appears in `_template/index.html`. The template already has it.
- **Look:** light only, never dark. Background `#FAFAF6`, text `#0A0A0A`, lime `#D4FF3F` used
  only for link underlines, hover and highlights. Font is Schibsted Grotesk. Keep it simple.
- **Charts:** series colours come from the variables in `assets/post.css` (`--s1` blue,
  `--s2` green, `--s3` magenta, `--neutral` grey). Do not introduce new chart colours.
- **Homepage lists:** each entry is a title link with the year on the right. Papers, Talks and
  Musings entries have a one-line description; Articles are titles only. Newest first. Update
  the section's count when adding or removing an entry.
- **Bio wording on the homepage is Dave's.** Do not rewrite it without asking.

## The Book of Mormon post

Its numbers and quoted text come from the public repository
`lifehug/book-of-mormon-authorship` (master copy: `paper/blog-phase1.html`). Do not change a
number by hand. The page's chart script is inline at the bottom of the file and must stay after
the content.

## Working on the site

- Preview locally with `python3 -m http.server 8000` from the repo root, then open
  http://localhost:8000. Paths such as `/assets/post.css` need a server; opening the file
  directly will not load them.
- More than one machine pushes here. Run `git pull --rebase` before every push.
- GitHub caches pages for about ten minutes; hard-refresh to see a change.
