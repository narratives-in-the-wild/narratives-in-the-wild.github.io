# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Development Commands

### Setup and Installation
- `bundle install` - Install Ruby gems and dependencies
- `bundle update` - Update all gems to latest compatible versions

### Local Development
- `bundle exec jekyll serve` - Start local development server at http://localhost:4000
- `bundle exec jekyll serve --drafts` - Include draft posts in development
- `bundle exec jekyll serve --incremental` - Enable incremental regeneration for faster builds
- `bundle exec jekyll build` - Build the site for production into `_site/` directory
- `bundle exec jekyll build --drafts` - Build including draft content

### Content Management
- `bundle exec jekyll post "Title"` - Create a new post (if jekyll-compose is installed)
- `bundle exec jekyll page "Title"` - Create a new page

## Project Context

This website is being developed to showcase the "Narratives in the Wild" research project - a collaborative narrative annotation infrastructure for social media platforms, specifically Bluesky. The research focuses on identifying and labeling "big, sticky stories" (narratives, tropes, frames) that spread online and contribute to misinformation ecosystems.

**Key Research Goals:**
- Build collaborative narrative labeling pipeline on Bluesky using moderation services
- Enable researchers, community members, and users to annotate posts with narrative labels
- Create open datasets for narrative research across disciplines
- Address misinformation through narrative understanding rather than fact-checking individual posts

## Architecture Overview

This is a Jekyll static site using the Jekyll Serif theme, currently set up as a professional services website template but needs to be customized for the research project. The site follows Jekyll's standard MVC-like architecture:

### Core Structure
- **Layouts** (`_layouts/`): Template structure files that wrap content
  - `default.html` - Base layout with HTML structure, navigation, footer
  - `home.html` - Homepage layout with services showcase and features
  - `page.html` - Standard page layout 
  - `service.html` - Individual service page template
  - `team.html` - Individual team member page template

### Content Architecture
- **Collections**:
  - `_services/` - Service offerings (e.g., accounting.md, tax-preparation.md)
  - `_team/` - Team member profiles with front matter for job titles, images
- **Data Files** (`_data/`):
  - `features.json` - Homepage feature highlights with icons
  - `menus.yml` - Site navigation structure (main & footer)
  - `contact.yml`, `social.json`, `seo.yml` - Configuration data

### Styling System
- **SCSS Architecture** (`assets/css/style.scss`):
  - Bootstrap 5.3.2 grid system (minimal components imported)
  - Custom color scheme: primary red (#e5261f), typography with Playfair Display
  - Component-based SCSS organization (`_sass/components/`)
  - Modular imports: only necessary Bootstrap components loaded for performance

### Key Configuration
- **Jekyll Config** (`_config.yml`):
  - Collections output enabled for services and team
  - Homepage service limit: 6 items
  - SCSS compression enabled
  - Jekyll environment variables plugin

### Deployment
- **Netlify** (`netlify.toml`):
  - Build command: `jekyll build`
  - Publish directory: `_site`
  - Ruby 3.2.2, production Jekyll environment

## Content Editing Patterns

### Adding Services
1. Create new `.md` file in `_services/` 
2. Include front matter: `title`, `date`, `weight` (for ordering)
3. Content automatically appears in homepage service grid and `/services/` listing

### Team Members  
1. Create new `.md` file in `_team/`
2. Front matter: `title`, `jobtitle`, `image`, `linkedinurl`, `weight`
3. Images should be placed in `images/team/`

### Navigation Updates
- Edit `_data/menus.yml` to modify main navigation or footer links
- Weight parameter controls display order

### Homepage Features
- Edit `_data/features.json` to modify the three feature boxes on homepage
- Each feature needs title, description, and icon image path

## Website Transformation Tasks

**Current State:** Generic business services website template
**Target:** Research project showcase for "Narratives in the Wild" study

### Content to Replace:
1. **Services** (`_services/`) - Replace accounting/business services with:
   - Research methodology sections
   - Annotation tools and processes
   - Collaboration frameworks
   - Technical infrastructure components

2. **Team** (`_team/`) - Replace with actual research team members

3. **Features** (`_data/features.json`) - Replace business features with:
   - Open annotation tools
   - Collaborative research infrastructure
   - Community involvement aspects

4. **Site Title & Branding** (`_config.yml`):
   - Update from "Jekyll Serif" to project name
   - Update logo and color scheme as needed

### Key Research Resources:
- Research paper source: `resources/2025_colm_nlp4democracy_bsky/colm2025_conference.tex`
- Project focuses on Bluesky platform narrative annotation
- Addresses misinformation through narrative analysis rather than fact-checking

## Development Notes

- Site uses minimal Bootstrap imports for performance (grid + utilities only)
- Custom hamburger menu component for mobile navigation  
- Responsive images with multiple breakpoint considerations
- SEO optimized with meta tags and Open Graph support
- Google Analytics integration via include file
