# Seiche Waves by Riya

A Jekyll site, free to host on GitHub Pages.

## 1. Repo setup

1. Create a GitHub repository named exactly `seichewavesbyriya`.
2. Upload everything in this folder to that repo.
3. Your site will be at: `https://RiyaNagar.github.io/seichewavesbyriya/`
   - If your GitHub username is different from `RiyaNagar`, open `_config.yml` and update the `url:` line to match.

## 2. Turn on GitHub Pages

1. Repo → **Settings → Pages**.
2. Source: **Deploy from a branch** → branch `main`, folder `/ (root)` → Save.
3. Wait 1–2 minutes, then visit the URL.

## 3. Add your real images

Replace these placeholder files in `assets/images/` with your own (keep the same filenames, or update the references in the relevant `.md` file if you rename them):

| Filename | Used for |
|---|---|
| `logo.png` | Koi fish icon, top-left of header |
| `profile.jpg` | Your portrait, homepage + About page |
| `waves-banner.jpg` | Wide quote banner on homepage |
| `essays-banner.jpg` | Banner image at top of Essays page |
| `memos-banner.jpg` | Banner image at top of Memos page |
| `placeholder-thumb.jpg` | Default thumbnail for any post that doesn't set its own `thumbnail` |

## 4. Set up Buttondown (newsletter)

1. Sign up free at buttondown.com.
2. Open `_includes/subscribe.html` and replace both instances of `YOUR_USERNAME` with your actual Buttondown username.

## 5. Adding a new piece of writing

Create a new `.md` file in the right folder — `_essays/`, `_memos/`, or `_papers/` — with this front matter at the top:

```yaml
---
title: "Your Title Here"
date: 2026-06-21
description: "One or two lines that show up in grid cards and lists."
tags: [China, Foreign Policy]
featured: false
thumbnail: /assets/images/your-image.jpg
---
```

Then write the piece in markdown below it.

- **`tags`**: use any tags you like. If you introduce a brand-new tag that doesn't have a page yet, see step 6.
- **`featured: true`**: only set this on posts you want in the homepage 3x3 grid. You control exactly which ones appear — it's not automatic.
- **`thumbnail`**: optional. If omitted, it falls back to `placeholder-thumb.jpg`.

The new post will automatically appear in: the relevant collection page (Essays/Memos/Papers) grid + list, Archives, and any tag page matching its tags. The only thing that does NOT update automatically is the homepage 3x3 grid — that only shows posts you've explicitly marked `featured: true`.

## 6. Adding a new tag

Tag pages are small individual files (one per tag), since Jekyll doesn't auto-generate them for custom collections without a plugin GitHub Pages doesn't support. To add a new tag, e.g. "Climate":

1. Create folder `tags/climate/`
2. Inside it, create `index.md`:
   ```yaml
   ---
   layout: tag
   title: "Climate"
   permalink: /tags/climate/
   ---
   ```
3. Use `Climate` (matching capitalization) in any post's `tags:` list.

## 7. Drafts

To keep a post unpublished, either:
- Save it outside the `_essays`/`_memos`/`_papers` folders (e.g. in a `_drafts-private/` folder you create) until ready, then move it in, **or**
- Add `published: false` to its front matter — Jekyll will exclude it from the built site entirely until you remove that line.

## Local preview (optional, needs Ruby)

```
gem install bundler jekyll
bundle init
echo 'gem "jekyll"' >> Gemfile
echo 'gem "jekyll-feed"' >> Gemfile
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000/seichewavesbyriya/` (note the path — it matches `baseurl`).

## Known limitation

This was built and checked for valid YAML and balanced template tags, but not run through an actual Jekyll build (no Ruby available in the build environment). If something errors on first deploy, paste the GitHub Pages build log error back and it can be fixed immediately — likely a small Liquid syntax issue if anything.
