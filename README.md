# msanchezmartinez.com

Personal website of Melchor Sanchez-Martinez, PhD: bio, publications and blog.
Built with [Jekyll](https://jekyllrb.com/) and published with GitHub Pages at <https://msanchezmartinez.com>.

Forked from [bbarad.github.io](https://github.com/bbarad/bbarad.github.io), a freely licensed personal website template (see `LICENSE`).

## Where things live

| What | Where |
| --- | --- |
| Bio text and profile links | `_bio/yo.md` (front matter drives the sidebar in `bio/index.html`) |
| Site name, description, URL | `_config.yml` |
| Top navigation | `_data/navlinks.yml` |
| Publications | `_data/publications.yml` (`scripts/europePMC_csv_to_yml.py` can generate entries) |
| Blog posts / drafts | `_posts/`, `_drafts/` |
| Header, footer, cookie banner, analytics | `_includes/` |
| CSS, JS, images, PDFs | `static/` |

## Run it locally

```bash
bundle install
bundle exec jekyll serve --future   # http://localhost:4000
```

## Deployment

Pushing to `master` triggers the GitHub Pages build and the `Jekyll site CI` workflow
(`.github/workflows/jekyll.yml`), which builds the site with the Gemfile's Jekyll version.
