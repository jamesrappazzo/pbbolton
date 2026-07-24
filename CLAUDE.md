# CLAUDE.md

Guidance for Claude Code working in this repository.

## What this is

**Phil Bolton's personal website** — a **Hugo** static site published at **pbbolton.com**.
This is a Hugo/Go-templates + Markdown project, **not** a JavaScript/TypeScript app — ignore
any global assumptions about React/Next.js/Prisma here.

- **Static site generator:** Hugo **extended**, pinned to **v0.146.7** (see
  `.github/workflows/hugo.yml`). Use a matching extended version locally.
- **Theme:** [`hugo-book`](https://github.com/alex-shpak/hugo-book), **vendored** as plain
  files under `themes/hugo-book/` (it is *not* a git submodule — there is intentionally no
  `.gitmodules`; don't reintroduce one).
- **Hosting:** GitHub Pages. `.github/workflows/hugo.yml` builds and deploys on every push to
  `main`. Custom domain `pbbolton.com` is set via `static/CNAME`.
- **Repo:** github.com/jamesrappazzo/pbbolton

## Who edits this and how (important context)

Phil is **non-technical** and edits **directly on github.com in the browser** — no local
clone, no terminal, no Markdown experience. He commits **straight to `main`**, and every commit
auto-deploys (~1–2 min). There are intentionally **no pull requests** — that flow was judged
too complex for him.

**`README.md` is Phil's plain-English editing guide.** You are usually invoked because Phil hit
something the guide couldn't get him past (a broken build, a missing image, a menu glitch). Fix
the immediate problem, keep changes minimal and obvious, and **if you change a convention, update
`README.md` to match** so his guide stays accurate.

Phil is told to only ever touch the `content/` folder, so a regression almost always originates
from a recent commit under `content/` — check `git log`/`git diff` there first. When you explain
a fix back to him, use plain language (his guide's vocabulary), not Hugo jargon.

## Content model

- `content/_index.md` — the homepage.
- `content/docs/` — everything here becomes the **left sidebar menu**, mirroring the folder
  tree.
  - **Sections** are folders with an `_index.md` holding `title` and `weight`
    (e.g. `content/docs/signal_processing/_index.md`).
  - **Articles are leaf bundles**: a folder with an `index.md`
    (e.g. `content/docs/signal_processing/preamp_73p/index.md`). **Images live in the same
    folder** and are referenced by bare filename. Keep this bundle structure — it's what makes
    images foolproof for a browser-only editor. Don't flatten articles back to single `.md`
    files.
- **Front matter** is YAML between `---` fences. `title:` sets the menu label and `<title>`;
  `weight:` orders the menu (**smaller = higher**). `draft` is not used. The commented
  `# bookXxx` lines in articles are optional hugo-book switches.

## Images, captions, embeds

- **Image:** `![alt/description](filename.jpg)` — file must be in the article's bundle folder;
  the reference is **case-sensitive**. Alt text is not visible on the page.
- **Image with a visible caption:** the built-in figure shortcode
  `{{< figure src="filename.jpg" caption="..." >}}`.
- **YouTube:** the built-in shortcode `{{< youtube VIDEO_ID >}}`.
- Raw HTML embeds are allowed: `markup.goldmark.renderer.unsafe = true` is set in `hugo.toml`.
- A **worked example** lives in `content/docs/signal_processing/haible_krautrock_phaser/` — a
  co-located image (`example-photo.svg`) shown via the figure shortcode. Use it as the reference
  pattern; the placeholder is meant to be swapped for a real photo.
- **`.HEIC` gotcha:** Phil is on iPhone, which shoots `.HEIC` by default — browsers won't render
  it. If a photo "won't show" and the filename ends in `.heic`/`.HEIC`, that's why; it needs to
  be a `.jpg`/`.png`.

## Build / preview / verify

```bash
hugo server        # local preview at http://localhost:1313
hugo               # one-off build into ./public (this is what CI runs, minified)
```

**Always run `hugo` after making changes and confirm it builds with no errors.** `public/`,
`resources/`, and `.hugo_build.lock` are gitignored — don't commit them.

## Troubleshooting playbook (why you're usually here)

Run `hugo` first — it reports the exact file and line for most failures.

- **Build fails / red ✗ on the GitHub commit (site won't update).** Most common cause is a
  **broken shortcode** — a `{{< figure ... >}}` or `{{< youtube ... >}}` missing a `"` quote or
  a `>`. Next most common is **malformed front matter** — a broken `---` fence or invalid YAML.
  Fix the character and rebuild.
- **Image not showing.** Filename mismatch (case-sensitive), the image isn't in that article's
  bundle folder, or it's a `.HEIC` file (browsers won't render it — convert to `.jpg`/`.png`).
  Hugo prints `WARN ... Image 'x' not found` during build — grep the build output.
- **Article missing from the menu / wrong name.** Check its front matter `title:` exists and the
  file is `.../<slug>/index.md` under `content/docs/`.
- **Menu items in the wrong order.** Adjust `weight:` (smaller floats up) in the relevant
  `index.md` / `_index.md`.
- **Revert a bad edit Phil made.** Prefer `git revert <sha>` (keeps history) for a pushed bad
  commit, or point him to the file's **History** on GitHub. Confirm before force-pushing.

## Deploy note

Pushing to `main` publishes to the live site. Only commit/push when asked; if it's a fix for
Phil, expect that push *is* the goal — but say so before doing it.
