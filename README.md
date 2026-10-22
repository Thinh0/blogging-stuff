# Thinh Writes

My personal blog — code, tech, sports, and whatever else is on my mind.
Built with [Jekyll](https://jekyllrb.com/), hand-themed, and deployed
automatically to [GitHub Pages](https://pages.github.com/) via GitHub Actions.

## Writing a new post

1. Add a Markdown file to `_posts/` named `YYYY-MM-DD-some-title.md`.
2. Give it front matter:

   ```yaml
   ---
   layout: post
   title: "Your title"
   subtitle: "Optional subtitle"       # optional
   categories: [code]                  # one of: code, tech, sports, life
   ---
   ```

3. Write the post in Markdown below the front matter.
4. Commit and push to `main` — the site builds and deploys automatically.

To add a new topic beyond `code` / `tech` / `sports` / `life`, add it to the
`categories` list in [`_config.yml`](_config.yml) and give it a color in
[`_sass/_variables.scss`](_sass/_variables.scss) (look for the `--tag-*`
variables) plus a `.tag--<slug>` rule in
[`_sass/_components.scss`](_sass/_components.scss).

## Running locally

Requires Ruby ≥ 3.0.

```bash
bundle config set --local path 'vendor/bundle'
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000.

## Deployment

Every push to `main` triggers [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml),
which builds the Jekyll site and publishes it to GitHub Pages. No manual
build step, no hosting bill.

**One-time setup required in the GitHub UI:** go to the repo's
**Settings → Pages** and set **Source** to **GitHub Actions**. After that,
every push to `main` deploys automatically — the live URL will be shown on
that same settings page (typically `https://<username>.github.io/<repo>/`).

If you'd rather the site live at the root domain (`https://<username>.github.io`
with no repo path), rename this repository to exactly `<username>.github.io`.

## Theme

The design is fully custom (no third-party Jekyll theme gem):

- `_layouts/` — page skeletons (`default`, `home`, `post`, `page`)
- `_includes/` — reusable partials (header, footer, tags, post cards, reading time)
- `_sass/` + `assets/css/main.scss` — the stylesheet, built around CSS variables
  so light/dark mode is just a palette swap (`_sass/_variables.scss`)
- `assets/js/theme-toggle.js` — the dark mode toggle, persisted in `localStorage`

Topic pills on the home page filter posts client-side by category, no page
reload required.
