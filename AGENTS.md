# Repository Guidelines

## Project Shape

This is a GitHub Pages personal blog based on Jekyll, with a legacy Grunt asset pipeline.

- Posts live in `_posts/`.
- Shared layouts live in `_layouts/`.
- Shared partials live in `_includes/`.
- Static assets live in `css/`, `js/`, `img/`, `pdf/`, and `pwa/`.
- Site-wide Jekyll settings live in `_config.yml`.
- LESS source files live in `less/`; generated CSS is written to `css/`.

## Local Commands

- `jekyll serve -w`: runs a local Jekyll preview with file watching.
- `npm run py3view`: serves the generated `_site` directory on port `8020` with Python 3.
- `npm run py3wa`: starts Grunt watch, Python preview, and Jekyll watch together.

This repository does not currently include a `Gemfile`, so local Jekyll setup depends on the machine's installed Ruby/Jekyll environment.

The `Gruntfile.js` appears to be legacy template wiring: it points at `js/by-blog.js` and `less/by-blog.less`, which are not present in this checkout. Do not assume `grunt` can rebuild the active `css/hux-blog.css` assets without checking the files first.

## Editing Notes

- Keep posts in the existing Jekyll front matter style used under `_posts/`.
- Prefer editing LESS in `less/` when changing theme styles, then run `grunt` to regenerate files in `css/`.
- If the Grunt pipeline is still mismatched, update `less/hux-blog.less`, `css/hux-blog.css`, and the active `css/hux-blog.min.css` together.
- Avoid unrelated rewrites of generated/minified assets unless the source asset was changed.
- Preserve existing static paths such as `/img/...` because pages are served from the GitHub Pages root.
- `_config.yml` contains some mojibake in existing Chinese comments/text. Be careful when editing that file; avoid broad re-encoding or cleanup unless specifically requested.

## Validation

For content-only changes, inspect the affected Markdown/HTML and run a local Jekyll preview when possible.

For style or JavaScript changes:

1. Run `grunt`.
2. Run `jekyll serve -w` or the repo's preview script.
3. Open the affected pages in a browser and check desktop and mobile widths.

## Git Notes

The default branch is `master`. The working tree may be behind `origin/master`; check with `git status --short --branch` before starting larger changes.
