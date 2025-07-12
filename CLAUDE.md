# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hugo PaperMod is a Hugo theme based on hugo-paper. This is a complete Hugo theme repository that provides a fast, clean, responsive theme for Hugo static sites. The project focuses on performance, customization, and modern web standards.

**Key Information:**
- Requires Hugo v0.146.0 or greater
- Written in Go templates with CSS and JavaScript assets
- No build tools (webpack, nodejs) required for theme development
- Uses Hugo's built-in asset pipeline for CSS/JS processing

## Development Commands

### Hugo Site Testing
```bash
# Create a new Hugo site to test the theme
hugo new site test-site
cd test-site
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
echo "theme = 'PaperMod'" >> hugo.toml

# Run development server
hugo server -D

# Build static site
hugo
```

### Theme Development
```bash
# No build process required - Hugo handles asset compilation
# CSS and JS files are processed automatically by Hugo's asset pipeline

# For testing theme changes, use with a test Hugo site
hugo server --source=test-site --themesDir=../
```

## Architecture

### Directory Structure
- `layouts/` - Hugo template files (HTML with Go templating)
  - `_default/` - Base templates (baseof.html, single.html, list.html)
  - `partials/` - Reusable template components
  - `shortcodes/` - Custom Hugo shortcodes
- `assets/` - Source assets processed by Hugo's pipeline
  - `css/core/` - Core theme styles (theme-vars.css, reset.css)
  - `css/common/` - Component styles (header.css, footer.css, etc.)
  - `css/extended/` - User customization area
  - `js/` - JavaScript files (search functionality)
- `i18n/` - Internationalization files (YAML format)
- `static/` - Static assets served directly (not present in this theme)

### Key Template Files
- `layouts/_default/baseof.html` - Base HTML structure
- `layouts/partials/head.html` - HTML head with asset pipeline logic
- `layouts/partials/header.html` - Site header component
- `layouts/partials/footer.html` - Site footer component

### CSS Architecture
- Uses CSS custom properties (CSS variables) for theming
- Light/dark theme support via CSS classes
- Asset concatenation and minification handled by Hugo
- Modular CSS structure with separate files for components

### Template System
- Uses Hugo's Go templating engine
- Extensive use of partials for modularity
- Conditional rendering based on site configuration
- Built-in SEO and performance optimizations

### Internationalization
- Multi-language support via i18n files
- YAML-based translation files in `i18n/` directory
- Language-specific content rendering

## Theme Configuration

The theme is configured through Hugo's site configuration (hugo.toml/yaml/json in the consuming site). Key parameters include:
- Theme selection and asset settings
- Analytics integration
- Social media configuration
- Feature toggles (search, TOC, etc.)

## Important Notes

- This is a Hugo theme, not a standalone site
- No package.json or npm scripts - uses Hugo's asset pipeline
- Theme must be used within a Hugo site structure
- CSS and JS are processed automatically by Hugo during build
- Development requires Hugo binary installed locally