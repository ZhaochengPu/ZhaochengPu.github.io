# Zhaocheng Pu — personal academic website

This repository contains the source for [zhaochengpu.github.io](https://zhaochengpu.github.io), built with [al-folio](https://github.com/alshedivat/al-folio) and GitHub Pages.

The first public version keeps four sections:

- about
- projects
- notes
- CV

Publications, talks, and teaching pages are intentionally omitted until there is real content for them.

## Update later

- Replace the public photos in `assets/img/` when you want to refresh them.
- Update public contact and social links in `_data/socials.yml`.
- Replace the draft CV data in `_data/cv.yml` and optionally enable PDF generation.

## Local validation

```bash
npm ci
npm run lint:prettier
bundle exec al-folio upgrade audit --no-fail
bundle exec jekyll build
```
