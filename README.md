# ApplyBoost

AI-Powered Job Application Automation - Landing Page

## Overview

ApplyBoost is a static marketing website for an AI-powered job application automation service. The site includes a landing page with features, testimonials, contact form, and legal documentation pages.

## Live Site

- **GitHub Pages:** https://empire-media.github.io/apply-boost/
- **Custom Domain:** (Configure your Namecheap domain)

## Files

- `index.html` - Main landing page
- `privacy.html` - Privacy Policy
- `terms.html` - Terms of Service
- `gdpr.html` - GDPR Compliance

## Local Development

Open `index.html` directly in a browser, or use a local server:

```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```

## Deployment

This site automatically deploys to GitHub Pages via GitHub Actions on every push to the `main` branch.

## Custom Domain Setup (Namecheap)

1. **Create CNAME file** in the repository root with your domain name

2. **Configure GitHub Pages:**
   - Go to Repository Settings → Pages
   - Enter your custom domain
   - Enable "Enforce HTTPS"

3. **Configure Namecheap DNS:**
   - Go to Domain List → Manage → Advanced DNS
   - Add A records pointing to GitHub Pages IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Add CNAME record: `www` → `empire-media.github.io.`

See `CLAUDE.md` for detailed development instructions.

## Technology Stack

- Pure HTML, CSS, JavaScript
- Google Fonts (Poppins, Inter)
- No build process required

## License

All rights reserved © 2025 ApplyBoost
