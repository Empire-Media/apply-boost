# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ApplyBoost is a static marketing website for an AI-powered job application automation service. The codebase consists of standalone HTML files with embedded CSS and JavaScript, serving as the landing page and legal documentation pages.

## Files Structure

- `index.html` - Main landing page with product features, testimonials, and contact form
- `privacy.html` - Privacy Policy page
- `terms.html` - Terms of Service page
- `gdpr.html` - GDPR compliance information page

## Architecture

### Single-Page Static Site
Each HTML file is completely self-contained with:
- Inline CSS using CSS custom properties (CSS variables) for theming
- Inline JavaScript for interactive features
- No external dependencies or build process required

### Design System

Color palette defined in CSS variables:
- Primary Orange: `#FF6B35`
- Deep Blue: `#004E89`
- Light Blue: `#1A8FE3`
- Consistent spacing scale and border radius values

Typography:
- Display font: 'Poppins' (headings)
- Body font: 'Inter' (content)
- Both loaded from Google Fonts

### Main Landing Page Features

1. **Fixed Navigation Bar**
   - Smooth scroll behavior for anchor links
   - Transparent backdrop with blur effect

2. **Hero Section**
   - Product introduction
   - Call-to-action buttons

3. **Features Section**
   - Six core features with icons and descriptions
   - AI capabilities, automation, customization

4. **How It Works**
   - Four-step process walkthrough

5. **Testimonials**
   - User success stories with avatars

6. **Contact Form**
   - Currently has placeholder submission logic (see line 1014-1059)
   - Form validation included
   - Mock API endpoint at line 1035 needs to be replaced with actual backend

### JavaScript Functionality

Located at the bottom of `index.html` (lines 981-1061):

1. **Smooth Scrolling** - Anchor links scroll smoothly to target sections
2. **Contact Form Handler** - Currently simulates submission with setTimeout; production implementation commented out at lines 1034-1058

## Development Workflow

### Viewing the Site
Open HTML files directly in a browser:
```bash
# Linux/Mac
xdg-open index.html  # or 'open' on macOS

# Or use Python's built-in server
python3 -m http.server 8000
# Then visit http://localhost:8000/index.html
```

### Making Changes

Since this is a static site with inline styles and scripts:

1. **CSS Changes** - Edit the `<style>` block in the `<head>` section
2. **Content Changes** - Edit HTML directly in the `<body>` section
3. **JavaScript Changes** - Edit the `<script>` block at the end of the file

### Testing

- Test all anchor navigation links
- Verify smooth scrolling behavior
- Test contact form submission (currently mocked)
- Check responsive design at different viewport sizes
- Validate HTML/CSS using W3C validators if needed

## Important Implementation Notes

### Contact Form Integration
The contact form at lines 934-949 requires backend integration. Current implementation (lines 1014-1059) is a mock. To implement:

1. Replace the setTimeout mock with the commented fetch call (lines 1034-1058)
2. Update `YOUR_API_ENDPOINT` with actual backend URL
3. Implement error handling for network failures
4. Add CSRF protection if needed

### Cross-Page Consistency
When editing styles or navigation:
- Maintain consistent header/logo styling across all pages
- Privacy, Terms, and GDPR pages share similar styling
- Color scheme should remain consistent with main landing page

### Legal Pages
The privacy.html, terms.html, and gdpr.html files contain legal text. When updating:
- Ensure legal review before publishing changes
- Maintain consistent formatting with main site
- Update "Last Updated" dates when content changes

## Deployment

### GitHub Pages
This site is deployed to GitHub Pages using GitHub Actions. The workflow file is located at `.github/workflows/deploy.yml`.

**Automatic Deployment:**
- Every push to the `main` branch triggers automatic deployment
- Site is available at: https://empire-media.github.io/apply-boost/

**Custom Domain Setup:**
1. Add a `CNAME` file in the root directory with your domain name
2. In GitHub repo settings → Pages → Custom domain, enter your domain
3. Enable "Enforce HTTPS"

### Namecheap DNS Configuration
To point your Namecheap domain to GitHub Pages:

**For apex domain (e.g., applyboost.com):**
1. Go to Namecheap Dashboard → Domain List → Manage → Advanced DNS
2. Add these A records:
   ```
   Type: A Record, Host: @, Value: 185.199.108.153
   Type: A Record, Host: @, Value: 185.199.109.153
   Type: A Record, Host: @, Value: 185.199.110.153
   Type: A Record, Host: @, Value: 185.199.111.153
   ```

**For www subdomain:**
3. Add CNAME record:
   ```
   Type: CNAME Record, Host: www, Value: empire-media.github.io.
   ```

**DNS propagation** can take up to 48 hours but usually completes within a few hours.
