# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Jekyll-based freelance portfolio and blog site built on the Beautiful Jekyll remote theme. The site showcases services, blog posts, and projects, targeting DevOps and cloud engineering freelance work.

## Development Commands

### Local Development
```bash
# Install dependencies
bundle install

# Run local server with live reload
bundle exec jekyll serve --livereload
# Site available at http://127.0.0.1:4000

# Build the site
bundle exec jekyll build
# Output in _site/ directory
```

### Docker Alternative
```bash
# Build and run via Docker
docker build -t jekyll-site .
docker run -p 4000:4000 -v $(pwd):/usr/src/myapp jekyll-site
```

## Architecture

### Theme Override Pattern
The site uses **Beautiful Jekyll** (v6.0.1) as a remote theme with minimal local overrides:

- **Base theme**: Loaded via `remote_theme: daattali/beautiful-jekyll@6.0.1` in `_config.yml`
- **No custom layouts**: All layouts (page, post, default, home) come from the Beautiful Jekyll theme
- **Styling**: Custom styles in `assets/css/custom-styles.scss` can be added via `site-css` config
- **Content-based customization**: Pages use Beautiful Jekyll's built-in layouts with frontmatter configuration

**Important**: Avoid creating custom `_layouts/` or `_includes/` directories as they will override the theme and break the design. Use Beautiful Jekyll's built-in features and layouts instead.

### Content Structure

#### Collections
- **Posts** (`_posts/`): Blog articles using `YYYY-MM-DD-title.md` naming convention
  - Layout: `post` (defined in `_layouts/post.html`)
  - Default image: `/assets/img/og-default.jpg`

- **Projects** (`_projects/`): Portfolio projects collection
  - Layout: `project` (defined in `_layouts/project.html`)
  - Default image: `/assets/img/project-default.jpg`
  - Output: true (generates individual pages at `/projects/:slug/`)

#### Data Files (`_data/`)
- `services.yml`: Defines freelance service offerings displayed on Services page
  - Structure: title, description, deliverables array, CTA with label/url
- `navigation.yml`: Optional navigation overrides (primary nav in `_config.yml`)

### Layouts and Components

**Beautiful Jekyll Layouts** (from theme):
- `page`: Standard page layout with optional title and subtitle
- `post`: Individual blog post with metadata, tags, and sharing
- `default`: Base template (rarely used directly)
- `home`: Blog feed layout (use for blog listing pages)

**Custom overrides**: Previously had custom layouts in `_backup_custom/` directory. These were removed to use Beautiful Jekyll's native layouts.

### Pagination

Uses **jekyll-paginate** (Beautiful Jekyll standard):
- 8 posts per page
- Pagination URL pattern: `/blog/page:num/`
- Accessible in templates via `paginator` object
- Pagination configured in `_config.yml` with `paginate` and `paginate_path`

### Navigation

Primary navigation defined in `_config.yml` under `navbar-links:` key using Beautiful Jekyll's format:
```yaml
navbar-links:
  Blog: "blog"
  Projects: "projects"
  Services: "services"
```

Use simple string values for single pages, or nested hashes for dropdown menus.

## Content Editing Guidelines

### Adding a Blog Post
1. Create `_posts/YYYY-MM-DD-slug.md`
2. Include frontmatter:
   ```yaml
   ---
   layout: post
   title: "Your Title"
   date: YYYY-MM-DD
   categories: [category]
   image: /assets/img/your-image.jpg  # optional
   ---
   ```

### Adding a Project
1. Create `_projects/project-slug.md`
2. Include frontmatter:
   ```yaml
   ---
   title: "Project Name"
   description: "Short description"
   image: /assets/img/project-image.jpg  # optional
   ---
   ```

### Modifying Services
Edit `_data/services.yml` following the existing structure with title, description, deliverables array, and CTA object.

## Configuration Notes

- **Site URL**: Set in `_config.yml` (`url` and `baseurl`)
- **Timezone**: America/Toronto
- **Contact form**: Uses Formspree endpoint (configured in `contact.md`)
- **SEO**: Handled by `jekyll-seo-tag` plugin
- **Syntax highlighting**: Rouge with Kramdown (GFM input)

## Deployment

- **GitHub Pages**: Requires GitHub Actions (uses non-whitelisted plugin `jekyll-paginate-v2`)
- **Traditional hosting**: Build with `bundle exec jekyll build`, serve `_site/` via Nginx/Apache
