# Editing your website

Hi Phil! This is the guide for updating **pbbolton.com**. You do everything right here on
this GitHub website in your web browser — no special software, no coding. Take your time,
you can't really break anything permanently.

---

## The one rule 🚦

**You only ever need the `content` folder.** That's where all your writing and photos live.
Everything else in this project is the machinery that runs the website — you never have to open
it. If you're ever unsure whether to touch something outside `content`, the answer is: don't
(and text James).

---

## Find your answer fast

Jump straight to what you need:

- **Change the words in an article that already exists** → [Task 1](#task-1-edit-an-article-that-already-exists)
- **Make text bold, or add a heading / list / link** → [Task 2](#task-2-how-to-format-your-writing) or the [copy-and-paste blocks](#-copy-and-paste-blocks)
- **Add a photo** (with or without a caption) → [Task 3](#task-3-add-a-photo-to-an-article)
- **Write a brand-new article** → [Task 4](#task-4-add-a-brand-new-article)
- **Add a YouTube video** → the [copy-and-paste blocks](#-copy-and-paste-blocks)
- **Change the order or the name of things in the menu** → [Task 5](#task-5-reorder-or-rename-things-in-the-menu)
- **Edit the homepage** → [Task 6](#task-6-edit-the-homepage)
- **Delete or rename an article or photo** → [Task 7](#task-7-delete-or-rename-an-article-or-a-photo)
- **Check whether my change actually worked** → [How do I know my change worked?](#how-do-i-know-my-change-worked)
- **Something looks wrong / a photo won't show / I made a mistake** → [If something looks wrong](#if-something-looks-wrong)

---

## How your website works (the 30-second version)

- All your writing lives in this GitHub project, in a folder called **`content`**.
- **Whenever you save a change here, the website rebuilds itself automatically.** Your change
  goes live at pbbolton.com in about **1–2 minutes**. (It's not instant — give it a minute.)
- "Saving" on GitHub is called **committing**. When you see a green **Commit changes** button,
  that's just the Save button. Every save is remembered forever, so nothing is ever truly lost.

**Three things to remember:**
1. Do all your editing at **github.com** (this site), signed in to your account.
2. After you save, **wait a minute or two**, then refresh pbbolton.com to see it.
3. If something looks broken and you can't fix it, don't panic — text James. Every version is
   saved and can be restored.

---

## Where your articles live

Click the **`content`** folder at the top of this page to look around. Here's the layout:

```
content
├── _index.md                     ← your homepage ("Hey, I'm Phil.")
└── docs
    ├── signal_processing          ← a section (shows in the left menu)
    │   ├── preamp_73p
    │   │   └── index.md           ← the article's text
    │   ├── haible_triple_chorus
    │   │   └── index.md
    │   └── ...
    └── other                      ← another section
        └── retropie_cabinet
            └── index.md
```

The important idea: **each article is a folder**, and inside it there's a file called
`index.md` that holds the words. Photos for that article go **in the same folder**. That's it.

---

## 📋 Copy-and-paste blocks

Grab whichever block you need, paste it in, and just change the words. You never have to
remember any of this — copying is the intended way to do it.

### The settings block (the top of every article)

Every article starts with a little **settings block** between two `---` lines. It tells the
site what to call the article and where to put it in the menu. Here it is on its own:

```
---
title: "Your Article Title"
weight: 10
---
```

How it works:
- Keep **both `---` lines** exactly as they are — they mark the start and end of the settings.
  (If you delete one, the page will look broken.)
- **`title:`** is the name shown in the left-hand menu and on the browser tab. Keep the
  quotation marks around it. → *Change this.*
- **`weight:`** is its position in the menu. **Smaller number = higher up the list.** So
  `weight: 1` sits above `weight: 2`. → *Change this to move the article up or down.*
- Some existing articles have extra **greyed-out lines starting with `#`** in their settings
  block (like `# bookToc: true`). Those are optional switches you don't need — just leave them
  alone.

### A whole new, blank article

Paste this in when you create a new article (see **Task 4**), then change the words:

```
---
title: "Your Article Title"
weight: 10
---
# Your Article Title

Write your opening paragraph here.

## First section

More writing goes here.
```

### A photo

Most of your articles will have photos. It's two steps: **upload the photo into the article's
folder** (see **Task 3**), then paste **one line** wherever you want it to appear:

```
![Describe what's in the photo](photo-name.jpg)
```

- Change `photo-name.jpg` to your photo's **exact** filename.
- The words in the brackets are a description (they help Google and screen-reader users) — they
  **don't** show on the page.
- Got several photos in one article? Just paste this line once for each, with the matching
  filename.

### A photo *with a caption underneath*

Want words shown **under** the photo? Use this instead:

```
{{< figure src="photo-name.jpg" caption="Words shown under the photo" >}}
```

- Change `photo-name.jpg` and the caption words.
- ⚠️ Keep all the `"` quote marks and the `<` `>` — if you delete one by accident, the page
  won't build. (You'd see a red ✗ on your save; just put it back, or text James.)

### A link

```
[the words people click](https://the-website.com)
```

### Bold and italic

```
This is **bold**, and this is *italic*.
```

### A bullet list

Leave a blank line above it, then put one `- ` at the start of each line:

```
- First thing
- Second thing
- Third thing
```

### A numbered list

```
1. First step
2. Second step
3. Third step
```

### A YouTube video

Paste this where you want the video, and swap in your video's ID. The ID is the part of the
YouTube address right after `watch?v=` — e.g. in `youtube.com/watch?v=abc123XYZ` the ID is
`abc123XYZ`:

```
{{< youtube abc123XYZ >}}
```

### A section heading

Use this to break a long article into parts:

```
## My section heading
```

### A whole new section (a new category in the left menu)

The left menu has categories like *Signal Processing* and *Other*. To add a new category,
create a **folder** inside `content/docs`, and inside that folder create a file named exactly
**`_index.md`** (note the underscore at the front) containing:

```
---
title: "My New Section"
weight: 3
---
```

Then add articles inside that folder the normal way (**Task 4**). *(This one's rare — if you're
not sure, just text James.)*

---

## Task 1: Edit an article that already exists

1. Click into the article's folder, e.g. `content` → `docs` → `signal_processing` →
   `preamp_73p`.
2. Click the file **`index.md`**.
3. Click the **pencil icon** (✏️) near the top right. Its tooltip says *"Edit this file."*
4. Now you can type. To see how it will actually look, click the **Preview** tab at the top
   of the editing box.
5. When you're happy, click the green **Commit changes…** button (top right).
6. A box pops up. Leave everything as-is and click the green **Commit changes** button.
7. Done! Wait 1–2 minutes, then refresh pbbolton.com.

---

## Task 2: How to format your writing

The text uses a simple formatting style called **Markdown**. You don't need to learn much —
here's basically everything:

| To do this…            | Type this…                                  |
|------------------------|---------------------------------------------|
| A new paragraph        | Just leave a **blank line** between them     |
| A section heading      | `## My section heading`                      |
| A smaller heading      | `### A smaller heading`                       |
| **Bold text**          | `**bold text**`                              |
| *Italic text*          | `*italic text*`                              |
| A bullet list          | `- first item` (one `- ` per line)           |
| A numbered list        | `1. first item` (one per line)               |
| A link                 | `[the words to show](https://the-address.com)` |
| A photo                | `![description of the photo](photo-name.jpg)` (see Task 3) |

A few tips:
- The **very first line** of each article starts with a single `#` — that's the big title at
  the top of the page. Leave it there; just change the words.
- Leave a **blank line** before a heading or a list, or it might not work.
- Capital letters, spaces, and spelling in filenames matter (see Task 3).

Here's a complete example of what a finished article looks like — you can copy this style:

```
---
title: "73P Preamp"
weight: 4
---
# 73P Preamp

This is a preamp I built over the winter. It's based on a classic design and
sounds **fantastic** on vocals.

## The build

I started with the power supply. A few notes:

- Used a toroidal transformer
- Point-to-point wiring
- Took about *three weekends*

![The finished front panel](front-panel.jpg)

More details are on the [original schematic](https://example.com/schematic).
```

> The block at the very top between the two `---` lines is just settings.
> **`title:`** is the name that shows in the left-hand menu.
> **`weight:`** controls the order in the menu (smaller number = higher up).
> Don't delete the `---` lines.

---

## Task 3: Add a photo to an article

Photos go **in the same folder as the article**, and then you mention them by filename.

**Step A — put the photo in the folder:**
1. Make sure the photo is a **`.jpg`** or **`.png`** file. → *iPhone tip:* iPhones often save
   photos as `.HEIC`, which most web browsers **can't display**. To avoid this, set
   **Settings → Camera → Formats → Most Compatible** before taking pics, or just take a
   screenshot of the photo (screenshots are always `.png`).
2. Rename your photo to something simple with **no spaces** — use dashes instead.
   Good: `front-panel.jpg`. Bad: `IMG 0423 (1).JPG`.
3. On GitHub, click into the article's folder (e.g. `content` → `docs` →
   `signal_processing` → `preamp_73p`) so you can see its `index.md` file.
4. Click the **Add file** button (top right) → **Upload files**.
5. Drag your photo into the box (or click *choose your files*).
6. Click the green **Commit changes** button.

**Step B — show the photo in the article:**
1. Open that folder's **`index.md`** and click the **pencil** (✏️) to edit.
2. Where you want the photo, add a line like this:
   ```
   ![A description of the photo](front-panel.jpg)
   ```
   The name in the parentheses must match your photo's filename **exactly** (capital letters
   and the `.jpg` / `.png` ending count). The words in the brackets are a description that helps
   Google and screen-reader users — they don't show on the page. **Want a visible caption under
   the photo?** Use the `{{< figure … >}}` block from the
   [Copy-and-paste blocks](#-copy-and-paste-blocks) section instead.
3. Click **Preview** to check it, then **Commit changes**.

That's it — the photo appears once the site rebuilds. A couple of tips:
- **Several photos in one article?** Upload them all into the folder, then add one `![…]` line
  for each, wherever you want them.
- Keep photos reasonably sized — a normal phone photo is fine; anything over ~25 MB won't
  upload through the website.

---

## Task 4: Add a brand-new article

1. First, copy the **"A whole new, blank article"** block from the
   [Copy-and-paste blocks](#-copy-and-paste-blocks) section above.
2. Go to the section you want the new article in (e.g. the `signal_processing` folder).
3. Click **Add file** (top right) → **Create new file**.
4. In the filename box at the top, type the folder name, then `/index.md`. For example:
   ```
   my-new-project/index.md
   ```
   Typing the `/` automatically makes it a folder for you.
5. Paste the block into the big box, then change the `title:`, the `# Your Article Title`
   heading, and the body. Pick a `weight:` number for where it should sit in the menu (smaller
   = higher up).
6. Click **Commit changes…** → **Commit changes**.
7. To add photos to it, follow **Task 3** (upload them into your new `my-new-project` folder).

---

## Task 5: Reorder or rename things in the menu

Everything in the left-hand menu is controlled by the settings block at the top of each file
(between the `---` lines):

- **Rename** a menu item: change the `title:` line.
- **Reorder** items: change the `weight:` number. **Smaller numbers appear higher up.**
  (The two big sections, *Signal Processing* and *Other*, each have their own `weight` too —
  it's in the `_index.md` file inside those folders.)

Edit the file, change the number or title, and **Commit changes** as usual.

---

## Task 6: Edit the homepage

The homepage is `content/_index.md`. Open it, click the **pencil** (✏️), change the text, and
**Commit changes**. Same as any other article.

---

## Task 7: Delete or rename an article or a photo

**To delete a photo or an article:**
1. Open the file — the photo, or the article's `index.md`.
2. Click the **trash-can icon** (🗑️) near the top right. Its tooltip says *"Delete this file."*
3. Click the green **Commit changes** button.
4. To remove a **whole article**, delete its `index.md`; you can delete any leftover photos in
   that folder the same way.

**To change what an article is *called*** (its name in the menu): you don't rename any files —
just change the `title:` line in its settings block (see [Task 5](#task-5-reorder-or-rename-things-in-the-menu)).

**To change an article's actual web address** (the folder name): this is rarely needed and a bit
fiddly, and it breaks any old links to that page — **text James** for this one.

---

## How do I know my change worked?

1. As soon as you commit, your change is **saved**. Give the site **1–2 minutes** to rebuild,
   then refresh **pbbolton.com**.
2. Want to be sure it's building? On the repo's front page, look just to the right of your most
   recent save:
   - a **green check ✓** means the site rebuilt and your change is live;
   - an **orange dot 🟠** means it's still building — wait a moment and refresh;
   - a **red ✗** means something in that save stopped the site from building (see below).

---

## If something looks wrong

- **My change isn't showing up.** Give it 2–3 minutes and refresh. The site rebuilds after
  every save, and it takes a moment.
- **My photo isn't showing.** 99% of the time the filename doesn't match. Check that the name
  in `![...](name.jpg)` is spelled **exactly** like the uploaded file — capital letters count —
  and that the photo is in the **same folder** as that article's `index.md`.
- **My save shows a red ✗ / the site won't update.** Usually a `{{< figure … >}}` or
  `{{< youtube … >}}` block is missing a `"` quote mark or a `>`. Fix that character, or undo
  the save. Plain writing and plain `![...]` photos can't cause this.
- **The Preview tab shows my photo or video as code / a broken image.** That's normal —
  GitHub's Preview can't run the website's photo and video blocks. They'll look right on the
  **live site** after you commit. Use Preview mainly to check your words, headings, and lists.
- **I started editing but changed my mind.** Nothing is saved until you click the green
  **Commit changes** button. Just leave the page (click the repo name at the top, or hit your
  browser's back button) and nothing happens.
- **I want to undo something I already saved.** Open the file and click **History** (top right)
  to see earlier versions — or simply text James, who can put any earlier version back in
  seconds.
- **I think I broke it.** You didn't break anything permanently — every save is stored. On the
  repo's main page there's a list of recent saves; a **green check ✓** means the site built
  fine and a **red ✗** means the last save had a problem. If you see a red ✗ or the site looks
  wrong, text James and he can undo it in seconds.

You've got this. 🎛️

---

<details>
<summary><strong>Technical notes (for James)</strong></summary>

- **Stack:** Hugo (extended, v0.146.7) + the `hugo-book` theme. Deploys to GitHub Pages via
  `.github/workflows/hugo.yml` on every push to `main`. Custom domain via `static/CNAME`.
- **Content model:** the left menu is generated from `content/docs/`. Articles are **leaf
  bundles** (`article/index.md`) so images can be co-located and referenced by bare filename —
  the simplest possible flow for a non-technical editor in the GitHub web UI.
- **Config:** `markup.goldmark.renderer.unsafe = true` is enabled in `hugo.toml` so pasted
  embed HTML (YouTube, etc.) isn't stripped. `archetypes/default.md` matches the real content
  style (YAML front matter, no `draft`).
- **Themes are vendored** (committed as plain files), *not* git submodules — the old
  `.gitmodules` was declaring submodules that didn't exist, so it was removed. The unused
  `PaperMod` theme was deleted. To update `hugo-book`, replace the files under
  `themes/hugo-book/`.
- Build artifacts (`public/`, `resources/`, `.hugo_build.lock`) are gitignored.
</details>
