<!-- Copilot / AI agent instructions for this repository -->
# Repository overview

This repository is a small Jekyll-based GitHub Pages site (see `_config.yml`). Markdown pages in the repo root and `case-studies/` are rendered through the `_layouts/default.html` template; CSS lives under `assets/css/style.css`.

# Big picture (how changes flow)

- Source: `.md` files (front matter + markdown) such as `index.md`, `portfolio.md`, `case-studies/*.md`.
- Layout: `_layouts/default.html` controls global HTML structure and sidebar navigation; it references `/assets/css/style.css` for styling.
- Build: Jekyll converts the Markdown + layouts into static HTML. The site is published via GitHub Pages using the `jekyll-theme-minimal` declared in `_config.yml`.

# Key files to reference

- `_config.yml` — site metadata, `nav` entries, `permalink: pretty`, `include: assets/css`, and plugins (`jekyll-feed`, `jekyll-seo-tag`).
- `_layouts/default.html` — primary template and sidebar navigation logic (note explicit URL checks like `page.url == '/portfolio.html'`).
- `case-studies/template.md` — canonical structure and front-matter pattern for new case studies.
- `assets/css/style.css` — global styling; edits here affect the entire site.

# Project-specific conventions (concrete, discoverable patterns)

- Pages use front matter keys `layout: default` and `title:`. Example page header:

```yaml
---
layout: default
title: API Integration
---
```

- Navigation is defined in `_config.yml` under `nav:` with target `.md` paths (e.g., `Case Studies: case-studies/index.md`). When adding a top-level nav item, update this list.

- The layout contains hard-coded URL comparisons (e.g. `/portfolio.html`, `/case-studies/template.html`). When renaming pages or changing `permalink` behavior, verify these comparisons and links still match the generated URLs.

# Build / preview (commands observed or implied)

- Typical local preview with Jekyll (Ruby + Bundler):

```
gem install bundler jekyll
bundle install    # if a Gemfile is present
bundle exec jekyll serve --livereload
```

- GitHub Pages will build the site automatically; the `_config.yml` plugins list is compatible with GitHub Pages.

# Common tasks for an AI editing agent (explicit examples)

- Add a new case study: create `case-studies/<slug>.md` using `case-studies/template.md` front-matter and content structure.
- Update navigation: edit `_config.yml` → `nav:`; ensure the linked path exists (e.g., `portfolio.md` or `case-studies/index.md`).
- Change styles: edit `assets/css/style.css` and verify layout in local `jekyll serve` preview.
- Update layout markup: change `_layouts/default.html` only when you must alter global structure; remember to update any page URL comparisons inside the template.

# Integration points & external dependencies

- GitHub Pages / Jekyll (theme `jekyll-theme-minimal`). No runtime back-end services are present.
- Plugins: `jekyll-feed`, `jekyll-seo-tag` (listed in `_config.yml`).

# When you’re uncertain

- Run a local build (`bundle exec jekyll build`) and inspect `_site/` to confirm generated paths and HTML.
- If edits affect navigation or permalinks, verify both the `_config.yml` `permalink` setting and any literal URL checks in `_layouts/default.html`.

# Small, prioritized checklist for edits

1. Use `layout: default` for standard pages.
2. For case studies, copy `case-studies/template.md` as the starting point.
3. Update `_config.yml` `nav:` for visible navigation changes.
4. Preview with `jekyll serve` before pushing.

If any section is unclear or you want more examples (e.g., a sample new case study file), tell me which area to expand.
