# Autodite Deployment Checklist

## Before you push to GitHub

### 1. Download and replace Unsplash images
The site currently loads three background images from Unsplash URLs. Download them and save locally:

| Current URL | Save as |
|---|---|
| `https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=1920&q=80` | `assets/hero-bg.jpg` |
| `https://images.unsplash.com/photo-1497366216548-37526070297c?w=1920&q=80` | `assets/approach-bg.jpg` |
| `https://images.unsplash.com/photo-1497366754035-f200968a6e72?w=1920&q=80` | `assets/final-cta-bg.jpg` |

Then find and replace these URLs in `index.html`:
- Line ~80: `url('https://images.unsplash.com/photo-1522071820081-009f0129c71c?w=1920&q=80')` → `url('assets/hero-bg.jpg')`
- Line ~146: `url('https://images.unsplash.com/photo-1497366216548-37526070297c?w=1920&q=80')` → `url('assets/approach-bg.jpg')`
- Line ~236: `url('https://images.unsplash.com/photo-1497366754035-f200968a6e72?w=1920&q=80')` → `url('assets/final-cta-bg.jpg')`

### 2. Create an OG image (1200x630px)
Save as `assets/og-image.jpg`. This is the preview image shown when your link is shared on LinkedIn, WhatsApp, etc. Use your brand colours (terracotta/cream), "Autodite" text, and a short tagline.

### 3. Set up Cloudflare Email Routing
In the Cloudflare dashboard for autodite.com:
1. Go to **Email → Email Routing**
2. Enable Email Routing (Cloudflare will add the required MX and TXT DNS records)
3. Add a routing rule: `hello@autodite.com` → your personal email address
4. You'll receive a verification email at your personal address — click to confirm

### 4. Privacy Policy & Terms (commented out for now)
The footer links are commented out. When you're ready, create these pages and uncomment the links in `index.html` (search for `<!-- <a href="/privacy"`).

## Deployment steps (from the earlier walkthrough)
1. `git init` → `git add .` → `git commit` → push to GitHub
2. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git
3. Build command: (leave blank) | Output directory: `/`
4. Add custom domain `autodite.com` and `www.autodite.com`
5. Set up redirect: `www.autodite.com` → `autodite.com` (301)
6. Set up `autodite.co.uk` forwarding (AAAA records + redirect rules)
7. SSL → Full (strict), Always Use HTTPS, Automatic HTTPS Rewrites
8. Security headers via Transform Rules
9. Enable Email Address Obfuscation under Security → Settings
