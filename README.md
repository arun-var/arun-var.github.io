## Quick start

1. Install Ruby (>= 3.0) and Bundler.
2. Install deps:

   ```bash
   bundle install
   ```

3. Run locally:

   ```bash
   bundle exec jekyll serve --livereload
   ```

4. Open http://127.0.0.1:4000

## Customize

- Edit `_config.yml` (title, author, links, collections).
- Navigation via `nav` in `_config.yml` or `_data/navigation.yml`.
- Services list in `_data/services.yml`.
- Blog posts in `_posts/`.
- Projects as a collection in `_projects/`.
- Styles in `assets/css/main.scss`.

## Deploy

- **GitHub Pages:** works best via GitHub Actions (since we use non-whitelisted plugins).

