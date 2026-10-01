# MaKaBaKa.github.io

> This is my personal blog — the content (posts, photos, resume, etc.) is for my own use only. That said, if you like the look of the **makabaka** theme, feel free to use it on your own Hugo site — see below.

## Using the makabaka theme (for everyone else)

The theme is maintained in its own repository, [hugo-theme-makabaka](https://github.com/Rexturnull/hugo-theme-makabaka), so it's unaffected by whatever I post here. Install it into your own Hugo site as a submodule:

```bash
git submodule add https://github.com/Rexturnull/hugo-theme-makabaka.git themes/makabaka
```

To pin to the original, cleanest version (before any customization), check out the tag:

```bash
cd themes/makabaka
git checkout v1.0.0
cd ../..
git add themes/makabaka
git commit -m "Pin makabaka theme to v1.0.0"
```

Then add this to your `hugo.toml`:

```toml
theme = "makabaka"
```

For full configuration details (avatar, bio, resume, social links) and page structure, see the theme repo's own [README](https://github.com/Rexturnull/hugo-theme-makabaka/blob/main/README.md). Everything below is my own notes for maintaining this blog.

## Previewing changes locally

```bash
hugo server
```

Open http://localhost:1313 — the page auto-reloads whenever you save a file.

## Changing your avatar

Open [hugo.toml](hugo.toml) and point `params.author.avatar` to your image:

```toml
[params.author]
    avatar = "/img/avatar.svg"
```

Drop your photo into `static/img/` (e.g. `static/img/me.jpg`), then update the path to `/img/me.jpg`.

## Changing your bio, title, and contact info

Still in [hugo.toml](hugo.toml), under `[params.author]` and `[params.social]`:

```toml
[params.author]
    name = "Your Name"
    title = "Your Title"
    bio = "A one-line description of yourself"
    resume = "/files/resume.pdf"   # Resume PDF, place it under static/files/

[params.social]
    github = "https://github.com/your-handle"
    email = "you@example.com"
    linkedin = "https://www.linkedin.com/in/your-handle"
    twitter = "https://x.com/your-handle"
```

Save the file and the sidebar updates automatically.

## Writing a new post

Create a new folder under `content/posts/` with an `index.md` inside:

```
content/posts/tech/my-new-post/index.md
```

`index.md` needs this front matter at the top:

```toml
+++
title = "My New Post"
date = 2026-10-01T09:00:00+08:00
tags = ["go", "notes"]
cover = "cover.svg"
summary = "A one-line summary of what this post is about"
+++

Write your content here (Markdown supported).
```

- The post's cover image and any images used in the body go in the **same folder** as `index.md` (e.g. `content/posts/tech/my-new-post/cover.svg`). Reference body images with `![alt text](filename.png)` — no need to worry about the path.
- Hierarchy/categorization comes from the **folder structure** itself: posts in the same folder are grouped together, and subfolders become subcategories (browsable as a tree under the "By Topic" tab on the Posts page).

## Tagging posts

The `tags = [...]` field in a post's front matter is its tag list — add as many as you like:


```toml
tags = ["go", "concurrency", "notes"]
```

- Tags are **flat** and separate from folder categories: folders decide where a post lives, tags are extra keywords you stick on top.
- Once set, tags automatically show up in: the tag cloud on the homepage, the tag chips on post cards, and the `/tags/` page (where you can select multiple tags to cross-filter posts).
- No need to manually create tag pages — Hugo generates them automatically.

## How many posts show on each page?

- **Homepage "Recent Posts"**: always shows the latest **6** posts.
- **Posts page "All Posts"**: no pagination — every matching post is listed **on a single page**, and you can filter by title using the search box above the list.

