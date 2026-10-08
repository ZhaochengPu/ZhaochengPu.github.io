# Zhaocheng Pu — personal website

This repository contains the source for [zhaochengpu.github.io](https://zhaochengpu.github.io), built with [al-folio](https://github.com/alshedivat/al-folio) and GitHub Pages.

The site has three sections:

- **About** (`_pages/about.md`): photo, a short hello, links, the latest certificate, and a few photos.
- **Projects** (`_pages/projects.md`): one card per file in `_projects/`.
- **Certificates** (`_pages/certificates.md`): one card per entry in `_data/certificates.yml`.

## How to update

- **Add a certificate:** save the image in `assets/img/certificates/`, then add an entry at the top of `_data/certificates.yml` (title, issuer, date, image, and the verify link). The newest one also shows on the About page.
- **Add a project:** copy `_projects/personal-website.md`, then change the title, description, status, `importance` (lower numbers show first), and text.
- **Change the photos:** the profile photo is `assets/img/zhaocheng-profile.jpg`. The "Moments" photos are listed at the top of `_pages/about.md` and live in `assets/img/moments/`. Remove location data from new photos before adding them.
- **Change the links:** edit `_data/socials.yml`. The buttons on the About page follow its order.
- **Change colors or fonts:** see the "Site customizations" section at the bottom of `assets/css/main.scss`. That file shadows the theme's stylesheet, so run `bundle exec al-folio upgrade overrides audit` after updating the theme gems.

Pushing to `main` rebuilds and deploys the site automatically through `.github/workflows/deploy.yml`.

## Local preview

```bash
bundle install
npm ci
bundle exec jekyll serve      # open http://localhost:4000
npm run lint:prettier
bundle exec al-folio upgrade audit
```
