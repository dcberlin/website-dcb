# DCB Website — Editor Guide

This guide is for contributors who want to add or update content on the [Diaspora Civică Berlin](https://diasporacivica.berlin) website. You don't need to know how to code — you just need to be comfortable editing text files and following a recipe.

> **Note:** For now this guide covers **adding a news article** and **adding a project**. 

---

## Adding a news article

A news article is a single text file. To add one, you create a new file in the right folder, fill in a few labels at the top, and write your article underneath. To make it easier, you can start by copying the content from an existing news article, and making edits to it.

### 1. Where to put the file

The website has three languages, and each one has its own news folder:

- Romanian → `content/romanian/news/`
- English → `content/english/news/`
- German → `content/german/news/`

If your article should appear on all three language versions of the site, create one file in **each** folder, with the text translated. If it only exists in one language, just create it there — the others won't show it.

### 2. Naming the file

Pick a short, descriptive filename ending with `.md`. Use lowercase letters and dashes instead of spaces. The filename becomes part of the article's web address, so keep it clean and avoid special characters.

Good examples:
- `public-viewing-romania-belgia.md`
- `campaign-on-the-rights-of-seasonal-workers.md`

Avoid:
- `Public Viewing.md` (spaces)
- `știri-iunie!.md` (special characters)

### 3. What goes inside the file

Every news article starts with a small block of labels (called the "front matter") between two `---` lines, followed by the actual article text. Here is a complete example:

```markdown
---
title: "Public Viewing România - Belgia"
description: "Invitație la vizionarea meciului România - Belgia de la Euro 2024, organizată de DCB la Astra Kulturhaus din Berlin."
date: 2024-06-13
draft: false
categories: ["Event"]
---

## Hai să ne uităm la meci împreună!

[Astra Kulturhaus](https://maps.app.goo.gl/ii2fJ7xsDKriXXQQ8) organizează public viewings pentru Campionatul European...

![Poster of the event](/images/news/2024/06/Public-Viewing-Videowand.jpg)
```

### 4. The labels at the top — what each one means

| Label | What it does |
|---|---|
| `title` | The headline shown at the top of the article and in the news list. Keep it inside double quotes. |
| `description` | A short summary used **only behind the scenes** — see the section below. It is **not** shown on the article page itself. |
| `date` | The publication date, in the format `YYYY-MM-DD`. Used to sort articles (newest first). |
| `draft` | Set to `false` to publish the article. Set to `true` if you're not ready yet — drafts won't appear on the live site. |
| `categories` | One or more tags in square brackets, e.g. `["Event"]` or `["Event", "Volunteering"]`. |
| `image` | (Optional) Path to a cover picture, e.g. `"/images/news/2020/09/photo.jpg"`. Used as the article banner, the listing thumbnail, and the social-media preview. See section 7. |

### 5. About the `description` field

The `description` is **not visible on the article page**. It's used in three places that most readers never look at directly, but that matter a lot:

1. **Search engines** (Google, etc.) — they often show this text as the snippet under the article's link in search results.
2. **Social media previews** — when someone shares the article link on Facebook, LinkedIn, WhatsApp, or similar, this is the text that appears below the title in the link preview.

**What to write:** one or two sentences (around 150 characters) summarising what the article is about and why someone should click. Write it as a hook for a stranger, not as a heading. If you leave it empty, the site will fall back to using the first part of the article body, which is usually less compelling.

### 6. About categories

Categories group related articles. They show up in three places on the site:

- Under the title on the article page itself
- In a "Categories" widget on the news sidebar, with a count next to each
- As filter pages — e.g. `/categories/event/` lists every article tagged "Event"

**Categories currently in use:**

- **Romanian:** `Articole`, `Event`, `Ce`
- **English:** `Articles`, `Event`, `What`
- **German:** `Artikel`

To see the existing categories, go to the News page and check the categories listed as available to filter by.

**How to use them:** add one or more names inside square brackets in the `categories:` line, separated by commas. Example: `categories: ["Event", "Articole"]`.

**Spelling and casing must match exactly** — "Event" and "event" would become two separate categories. The safest habit is to copy the line from an existing article.

#### Adding a new category that works across all languages

There is no central list of categories: Hugo creates one automatically the first time you use a name, and it does it separately per language. That means a "Volunteering" category in English and a "Voluntariat" category in Romanian are unrelated as far as the site is concerned — keeping them in sync is up to the editors.

To introduce a new category in all three languages:

1. **Pick a name in each language.** For example:
   - Romanian: `Voluntariat`
   - English: `Volunteering`
   - German: `Freiwilligentätigkeit`

   You can also reuse the same word across languages if it reads naturally — that's what currently happens with `Event`, which appears in both the Romanian and English articles unchanged.
2. **Use that exact name consistently** in the `categories:` field of every article in that language, from then on. Avoid variations in spelling, casing, or accents.
3. **Write it down somewhere shared** (this README, a team note) so other contributors use the same names. Without a shared reference, it's easy to end up with `Voluntariat` and `voluntariat` as two separate categories by accident.

When the site is rebuilt, the new category page and a new entry in the sidebar widget will appear automatically.

### 7. About the cover image

You can add an `image:` line to the front matter, pointing to a picture stored under `static/images/`:

```
image: "/images/news/2020/09/seasonal-workers.jpg"
```

This is the article's "main" picture, and it is reused in **four** places — so picking a strong one matters more than any image you add inside the body:

- **The article page** — shown as a banner above the title.
- **The news list** — used as the thumbnail on the card that links to the article. If you don't set an `image`, the site falls back to a generic placeholder, which makes the card look bland.
- **Social-media previews** — when the link is shared on Facebook, LinkedIn, WhatsApp, etc., the preview shows this image next to the title and description.
- **Search engines** — they may show this picture next to the article in search results and pick it up as the article's "main image" in structured data.

**Tips:**

- Prefer a horizontal (landscape) image — preview cards crop tall ones badly.
- Make sure the file actually exists at the path you wrote, and that the path starts with `/images/...`.
- The `image:` field is **separate** from pictures you place inside the article body. Inline images (`![alt](/images/...)`) only show up where you write them in the text — they don't become the cover. If you want the same picture as both the cover and the first image in the article, you have to add it in both places.

### 8. Writing the article body

Everything **after** the second `---` is the article itself. It uses Markdown, a simple formatting language. The basics:

- `## Heading` — a section heading (use `###` for smaller subheadings).
- `**bold**` and `*italic*` for emphasis.
- `[link text](https://example.com)` — a clickable link.
- `![alt text](/images/path/to/picture.jpg)` — an image.
- An empty line between paragraphs separates them.
- A list:
  ```
  - first item
  - second item
  ```

You can search online more about the markdown syntax, or start [here](https://markdowncheatsheet.com/reference).

### 9. Adding images

Place image files for news articles inside `static/images/news/`, organised by year and month (e.g. `static/images/news/2024/06/`). Then reference them in the article with a path that starts with `/images/news/...`.

Example:
```markdown
![Volunteers at the event](/images/news/2024/06/public-viewing.jpg)
```

Try to keep images reasonably sized (under ~500 KB each) so pages load quickly.

### 10. Publishing

Once your `.md` file is saved in the right folder with `draft: false`, the article will appear on the news page the next time the site is built and deployed. If something doesn't show up, the most common causes are:

- `draft: true` is still set
- The `date` is in the future
- The file isn't in `content/<language>/news/`
- The filename has spaces or special characters

---

## Adding a project

A project works almost exactly like a news article: a single text file with a few labels at the top and the project description underneath. The easiest way to start is to copy an existing project (for example `club-de-carte.md`) and edit it.

The main differences from news articles are: projects live in their own folder, they can be marked as **ongoing**, they can have a **photo gallery**, and they don't use categories.

### 1. Where to put the file

Each language has its own projects folder:

- Romanian → `content/romanian/projects/`
- English → `content/english/projects/`
- German → `content/german/projects/`

As with news, create one file in **each** folder (translated) if the project should appear in all three languages, or only in the languages where it exists.

### 2. Naming the file

Same rules as for news: short, lowercase, dashes instead of spaces, ending in `.md`. The filename becomes part of the project's web address.

Good examples:
- `club-de-carte.md`
- `the-climate-lottery.md`

Don't name your file `_index.md` — that file is special and holds the text of the Projects page itself.

### 3. What goes inside the file

Here is a complete example:

```markdown
---
title: "Clubul de Carte DCB"
description: "Un club de carte informal pentru românii din Berlin – fără lectură comună impusă."
date: 2026-04-19
draft: false
ongoing: true
image: "/images/projects/2026/club-de-carte.jpg"
---

Clubul de Carte DCB este un spațiu informal pentru românii din Berlin care vor să discute despre cărți...

Vezi mai multe detalii și înscrie-te pe [meetup](https://www.meetup.com/diaspora-civica-berlin/).
```

### 4. The labels at the top — what each one means

| Label | What it does |
|---|---|
| `title` | The project name, shown on the project page, on its card in the projects list, and in the slider on the home page. Keep it inside double quotes. |
| `description` | (Optional, but recommended) A short summary for search engines and social-media previews. It is **not** shown on the page. Works exactly like the news `description` — see [About the `description` field](#5-about-the-description-field). |
| `date` | The project's date, in the format `YYYY-MM-DD` (usually when it started or took place). Used to sort projects, newest first. |
| `draft` | `false` to publish, `true` to keep it hidden from the live site. |
| `ongoing` | (Optional) Set to `true` if the project is still running. See section 5. Leave it out for past projects. |
| `image` | (Optional, but strongly recommended) The main picture of the project, e.g. `"/images/projects/2026/club-de-carte.jpg"`. See section 6. |
| `thumbnail` | (Optional) A different picture used **only** on the project's card in lists. See section 6. |
| `gallery_images` | (Optional) A list of extra pictures shown in a "Gallery" at the bottom of the project page. See section 7. |

### 5. Ongoing vs. past projects

The Projects page can show filter buttons — **All**, **Ongoing Projects** and **Past Projects**.

- Add `ongoing: true` to the front matter of projects that are still active (a recurring club, a running campaign, etc.).
- Leave the line out (or set `ongoing: false`) for projects that are finished — they automatically count as "past".
- The filter buttons only appear if at least one project is marked as ongoing.

When a project ends, remember to remove the `ongoing: true` line (in every language) so it moves to "Past Projects".

### 6. About the cover image and thumbnail

The `image:` picture is used:

- **On the project page** — as a banner above the title.
- **On the project's card** — in the projects list and in the home-page slider (unless a `thumbnail` is set).
- **In social-media and search previews.**

If you don't set an `image`, the card shows a generic placeholder.

The card is a fixed-size box, so the picture gets cropped to fit. If your cover image doesn't crop well (for example a tall poster where the important text gets cut off), you can add a separate `thumbnail:` picture for the card only:

```
image: "/images/projects/2026/Cafeneaua-Civica-Kantine.jpg"
thumbnail: "/images/projects/2026/Cafeneaua-Civica-Kantine-thumbnail.webp"
```

The project page will still use `image` as its banner; only the card changes.

Store project pictures under `static/images/projects/`, organised by year (e.g. `static/images/projects/2026/`), and reference them with a path starting with `/images/projects/...`. As with news, keep images under ~500 KB and prefer landscape pictures.

### 7. Adding a photo gallery

To show a set of photos at the bottom of the project page, put them in their own folder under `static/images/projects/galleries/`, named after the project — e.g. `static/images/projects/galleries/1st-december-with-dcb/` — and list them in the front matter:

```markdown
---
title: "1st December with DCB"
date: 2017-12-01
draft: false
image: "/images/projects/galleries/1st-december-with-dcb/01.jpg"
gallery_images:
  - "/images/projects/galleries/1st-december-with-dcb/01.jpg"
  - "/images/projects/galleries/1st-december-with-dcb/02.jpg"
  - "/images/projects/galleries/1st-december-with-dcb/03.jpg"
---
```

Each picture goes on its own line, starting with two spaces, a dash and a space (`  - `). The indentation matters — if it's off, the site may fail to build. The pictures are shown in the order you list them, under a "Gallery" heading.

You can reuse one of the gallery pictures as the cover `image`, as in the example above.

### 8. Writing the project text

Everything after the second `---` is the project description, written in Markdown — exactly like a news article (see [Writing the article body](#8-writing-the-article-body)).

The first lines of the text are also used as the short preview on the project's card (about 150 characters), so start with a sentence that explains what the project is.

### 9. Publishing

Once the file is saved in `content/<language>/projects/` with `draft: false`, the project will appear on the Projects page — and, if it's among the 7 most recent, in the projects slider on the home page — the next time the site is built and deployed. If it doesn't show up, check:

- `draft: true` is still set
- The `date` is in the future
- The file isn't in `content/<language>/projects/`
- The filename has spaces or special characters
- The indentation of `gallery_images` is wrong (this can break the build)

---
