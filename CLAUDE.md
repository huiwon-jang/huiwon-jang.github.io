# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Academic homepage for Huiwon Jang (KAIST PhD student), hosted via GitHub Pages at `huiwon-jang.github.io`. Built with Jekyll (no `_config.yml` or `Gemfile` — uses GitHub Pages defaults with the Skeleton CSS framework).

## Architecture

### Main site (Jekyll-based)

- `index.html` — Main page content using `layout: default`. Sections: About, Publications, Education, Experience, Academic Services, Honors & Awards, Invited Talks.
- `_layouts/default.html` — Base HTML template. Loads profile info from `site.data.main_info`, includes navbar, footer, and Google Analytics.
- `_layouts/project.html` — Template for individual project pages (extends default).
- `_data/main_info.yaml` — Name, title, email, profile pic path, CV path, social links.
- `_data/publications.yaml` — All papers with metadata (title, authors, venue, links, `selected: y/n` flag).
- `_data/experience.yaml` — Work/school experience entries.
- `_data/projects.yaml` — Project entries (currently a placeholder).

### Publication filtering

Publications use a tab UI (Selected / All). The `selected` field in `publications.yaml` controls which papers appear in the "Selected" tab. Author name is bolded+underlined via `<b><u>` HTML in the YAML.

### Project pages (standalone HTML)

`contextvla/` and `coordtok/` are standalone project pages — they do **not** use Jekyll layouts. They use the Bulma CSS framework (not Skeleton), MathJax for equations, and their own `static/` directories for assets (CSS, JS, images, videos). These pages follow the [Nerfies template](https://github.com/nerfies/nerfies.github.io) pattern common in ML research.

### Frontend libraries

- `libs/external/skeleton/` — Skeleton CSS grid (main site)
- `libs/external/font-awesome-4.7.0/` — Icons (main site)
- `libs/external/academicons-1.8.6/` — Academic icons (Google Scholar, etc.)
- `libs/external/skeleton_tabs/` — Tab switching for publication filters
- `libs/custom/my_css.css` — Main site custom styles (container max-width 800px, navbar, paper cards)
- `libs/custom/my_js.js` — Smooth scroll, sticky navbar, popover handling
- `stylesheet.css` — Lato font-face declarations and base typography

## Common tasks

**Local preview:** Run `jekyll serve` or `bundle exec jekyll serve` (requires Ruby + Jekyll installed). Project pages (`contextvla/`, `coordtok/`) can be previewed by opening their `index.html` directly in a browser since they are standalone.

**Adding a publication:** Add an entry to `_data/publications.yaml`. Set `selected: y` to feature it on the default tab. Use HTML for author links and bold/underline formatting.

**Adding a project page:** Create a new directory (e.g., `projectname/`) with its own `index.html` and `static/` assets. Project pages are self-contained and do not depend on Jekyll data files.

**Deployment:** Push to `main` branch. GitHub Pages builds and deploys automatically.
