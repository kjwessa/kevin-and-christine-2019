# Kevin & Christine 2019 Wedding Site

## Overview
This repository contains the static website celebrating Kevin and Christine's 2019 wedding. The project began as a Webflow design that was exported and committed to Git. It has since been migrated to Cloudflare Workers with modern tooling for linting, formatting, and analytics. Every HTML page, stylesheet, script, image, and font lives in the repo so the site can be deployed as a complete static asset collection.

## Key features
- **Informational hub:** Dedicated pages share ceremony details, registry links, travel information, and stories about the couple and their wedding party.
- **Responsive layout:** The markup preserves responsive breakpoints, interactions, and typography choices so the site scales gracefully from phones to desktops.
- **Cloudflare Workers deployment:** Configured with `wrangler.jsonc` for deployment to Cloudflare Workers with automatic clean URLs and global CDN caching.
- **Modern tooling:** Uses Biome for linting and formatting, with pnpm as the package manager.
- **SEO optimized:** Includes sitemap.xml, robots.txt, and proper canonical URLs.
- **Analytics:** Integrated with PostHog for event tracking and user analytics.

## Repository structure

| Path | Purpose |
| --- | --- |
| `index.html` | Landing page with a summary of the wedding weekend and prominent calls to action. |
| `the-couple.html`, `our-guests.html`, `our-registry.html`, `our-wedding.html`, `contact-us.html` | Supporting pages with bios, schedules, RSVP guidance, travel tips, registry links, and contact information. |
| `css/` | Stylesheets including base styles, responsive overrides, and component-specific rules. |
| `js/` | JavaScript bundles that power interactions (menus, animations, sliders). |
| `images/` | Compressed hero images, gallery photography, icons, and favicons used across the pages. |
| `fonts/` | Self-hosted font files that ensure typography remains consistent. |
| `wrangler.jsonc` | Cloudflare Workers configuration for deployment, static asset serving, and clean URLs. |
| `biome.json` | Biome configuration for linting and code formatting. |
| `package.json` | Project dependencies and scripts for linting/formatting. |
| `sitemap.xml` | XML sitemap for search engine crawlers. |
| `robots.txt` | Robots file for search engine directives. |
| `.assetsignore` | Files to exclude from Cloudflare Workers deployment. |

## Getting started

### Prerequisites
- [pnpm](https://pnpm.io/) - Fast, disk space efficient package manager
- [Node.js](https://nodejs.org/) - JavaScript runtime
- [Wrangler](https://developers.cloudflare.com/workers/wrangler/) - Cloudflare Workers CLI

### Local development

1. **Clone the repository**
   ```bash
   git clone https://github.com/kjwessa/kevin-and-christine-2019.git
   cd kevin-and-christine-2019
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Run local development server**
   ```bash
   npx wrangler dev
   ```
   Visit `http://localhost:8787` in your browser.

   Alternatively, use any static file server:
   ```bash
   # Python 3 built-in server
   python3 -m http.server 5500

   # Node.js http-server (install globally first: npm install -g http-server)
   http-server -p 5500
   ```

## Development workflow

### Linting and formatting
The project uses [Biome](https://biomejs.dev/) for linting and code formatting:

```bash
# Check for issues
pnpm run check

# Auto-fix issues
pnpm run fix
```

### Updating content and assets
The HTML files are the canonical source of truth. When updating content:

1. Edit text or links within the relevant `.html` file.
2. Replace or add assets under `images/`, `css/`, or `js/` directories.
3. Verify that image dimensions and filenames match the references in the HTML.
4. Run `pnpm run check` to ensure code quality.
5. Preview locally with `npx wrangler dev`.
6. Commit the changes and deploy.

## Deployment

### Cloudflare Workers (recommended)
The site is configured for deployment to Cloudflare Workers:

```bash
# Deploy to production
npx wrangler deploy
```

The `wrangler.jsonc` configuration handles:
- Static asset serving from the root directory
- Clean URLs (automatic .html extension removal)
- Global CDN caching
- Free hosting for static content

### Alternative hosting
The site can also be deployed to other static hosts:
- **Netlify / GitHub Pages:** No build command needed, just point to the repository
- **Cloudflare Pages:** Direct upload or Git integration
- **Custom hosting (S3, etc.):** Upload all files with appropriate MIME types

For all hosts, HTTPS is recommended.

## Technologies

- **Hosting:** Cloudflare Workers
- **Analytics:** PostHog
- **Package Manager:** pnpm
- **Linting/Formatting:** Biome
- **SEO:** sitemap.xml, robots.txt, canonical URLs

## Maintenance tips
- **Accessibility & performance:** Run Lighthouse audits after significant content updates to verify color contrast, alt text coverage, and load times.
- **Version history:** Use descriptive commit messages when adjusting wording, photos, or schedule details.
- **Analytics:** Monitor PostHog dashboard for visitor insights and engagement metrics.

## Site design
Site design by [Brewww Studio](https://brewww.studio/)

## Contact
Questions or requests for updates can be handled by opening an issue in the repository.


