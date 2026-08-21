# fumbletable.github.io — retired

**This site is retired. Fumble Table lives at [fumbletable.com](https://fumbletable.com).**

It served the Jekyll + Chirpy version of Fumble Table until **April 2026**, and stayed
live as a duplicate of the whole blog for four months after the new site launched —
competing with fumbletable.com in search and confusing anyone arriving on an old link.
Retired **2026-08-21**.

## What's left here

Two files, and nothing else:

- `index.html` — forwards the root to fumbletable.com
- `404.html` — GitHub Pages serves this for **every** unmatched path, so every old URL
  gets forwarded. Old posts lived at `/posts/{slug}/`; the live site serves the bare
  slug at `/{slug}/` via the legacy redirect stubs added on 2026-07-30, so the redirect
  preserves the path and lands on the real article rather than dumping everyone on the
  homepage.

Old URLs now return **404 with a forward**, which is the intended outcome: search engines
drop the duplicate, humans land on the right page.

## What was removed, and why it mattered

The Jekyll site itself — `_posts/` (48 posts), `_tabs/`, `_data/`, `_plugins/`, `assets/`,
`tools/`, `_config.yml`, `Gemfile` — plus the Chirpy build workflow. **All of it is in git
history** (see the commit before the retirement) and all 48 posts live on fumbletable.com.

Also removed: **the Chirpy build workflow**, replaced with a plain static upload. Left in
place it would have failed on the missing `_posts` and deployed nothing — which would have
left the *old* site serving. That failure mode looks like success from the outside.

**`CNAME`** (which contained `fumbletable.com`) was already deleted on `main` in April —
commit `348ebf9`. Worth knowing it's gone: while it existed it was a dormant claim on the
live domain that a rebuild could have tried to re-assert.

One related thing that is **not** in this repo: the old Chirpy **PWA service worker**
outlived the site, so browsers that visited before April kept serving a cached March
snapshot of fumbletable.com. `public/sw.js` on the new site is a permanent kill-switch for
it — **do not delete that file**, stale clients still turn up.

## Do not un-retire this

If Fumble Table ever needs a GitHub Pages presence again, make a new repo. Bringing this
one back recreates the duplicate-content problem and the `CNAME` conflict in one move.

Brain context: `projects/fumble-table-site/PROJECT.md`.
