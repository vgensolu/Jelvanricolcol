# Jelvan Ricolcol - Portfolio Website Setup Guide

## Overview
This is a professional HR portfolio website built with HTML, Tailwind CSS, and JavaScript.

## Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Internet connection (for Tailwind CSS CDN)
- Web server or hosting platform

## Viewing the Website

### Option 1: Direct File Opening (Limited Functionality)
You can open `JelvanWebsiteNew.html` directly in your browser, but some features may not work correctly due to CORS restrictions.

### Option 2: Local Web Server (Recommended)
Use a local web server to view the website with full functionality:

```bash
# Using Python 3
python3 -m http.server 8000

# Using Python 2
python -m SimpleHTTPServer 8000

# Using Node.js (if you have http-server installed)
npx http-server -p 8000
```

Then open your browser and navigate to: `http://localhost:8000/JelvanWebsiteNew.html`

### Option 3: Deploy to Web Hosting
Upload the HTML file to any web hosting service:
- GitHub Pages
- Netlify
- Vercel
- Traditional web hosting (cPanel, etc.)

## Troubleshooting

### Issue: Website appears unstyled (plain white background with basic text)

**Symptoms:**
- No colors, gradients, or visual styling
- Plain white background
- Basic HTML structure only

**Common Causes:**

1. **Ad Blocker or Browser Extension Blocking CDN**
   - Some ad blockers (uBlock Origin, AdBlock Plus, etc.) block CDN resources
   - **Solution:** Whitelist `cdn.tailwindcss.com` in your ad blocker or temporarily disable it for this site

2. **Content Security Policy (CSP) Restrictions**
   - Some environments have strict CSP that blocks external scripts
   - **Solution:** Configure CSP to allow `cdn.tailwindcss.com`

3. **No Internet Connection**
   - Tailwind CSS is loaded from a CDN and requires internet access
   - **Solution:** Ensure you have an active internet connection

4. **Firewall or Network Restrictions**
   - Corporate or institutional firewalls may block CDN access
   - **Solution:** Contact your IT department to whitelist `cdn.tailwindcss.com`

### Converting to Self-Hosted Tailwind CSS (Advanced)

If you need to work offline or avoid CDN dependencies:

1. Install Tailwind CSS via npm:
```bash
npm install tailwindcss
```

2. Create a `tailwind.config.js` file

3. Build your CSS:
```bash
npx tailwindcss -i ./input.css -o ./output.css --watch
```

4. Replace the CDN script tag with:
```html
<link href="./output.css" rel="stylesheet">
```

## Browser Compatibility
- Chrome/Edge: ✅ Fully supported
- Firefox: ✅ Fully supported
- Safari: ✅ Fully supported
- Internet Explorer: ❌ Not supported (use modern browser)

## Features
- Responsive design (mobile, tablet, desktop)
- Interactive service wheel
- Smooth scrolling navigation
- Contact form with validation
- Animated transitions and effects
- Privacy policy modal
- GDPR-compliant data handling notice

## Technical Stack
- **HTML5**: Semantic markup
- **Tailwind CSS 3.x**: Utility-first CSS framework (via CDN)
- **Vanilla JavaScript**: No framework dependencies
- **SVG Icons**: Inline vector graphics for scalability

## Notes
- The website is designed to be self-contained in a single HTML file
- All JavaScript and custom CSS are inline for portability
- External dependencies: Only Tailwind CSS CDN

## Support
For issues or questions about the website, please refer to the contact information in the portfolio.

## License
© 2025 Jelvan Ricolcol. All rights reserved.
