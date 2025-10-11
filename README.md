# Omnivorous Labs — Starter Kit

## Contents
- `index.html` / `styles.css` — minimal, clean single-page site.
- `assets/logo.svg` — simple prism/beam logo placeholder.
- `_redirects` — Netlify-style redirects to force HTTPS and consolidate sibling domains.
- `dns_templates.yaml` — sample DNS for hosting + email providers.
- `email_migration_checklist.md` — step-by-step plan to switch mail providers safely.

## Deploy (Netlify, easiest)
1) Create a new site on Netlify.
2) Drag-and-drop the folder or push to a repo and connect.
3) Add your custom domain `omnivorouslabs.com` and Netlify will guide DNS.
4) Ensure HTTPS is enabled (Let's Encrypt auto).

## Deploy (Vercel, also easy)
1) Create a new project and import the folder/repo.
2) Add `omnivorouslabs.com` as the domain and follow DNS prompts.
3) Set the apex to A/ALIAS and `www` CNAME as guided.

## DNS Tips
- Use Cloudflare Free for DNS and SSL termination if you want a neutral host-agnostic layer.
- Start DMARC with `p=none` to monitor; switch to `quarantine`/`reject` after a week or two of good mail.

## Branding Notes
- Primary colors: Deep Navy `#0B1E33`, Accent Neon Green `#A8FF3B`, Muted Gray `#5B6B7C`.
- Typeface: Inter (Google Fonts) or any modern geometric sans serif.
- Tagline lockup: “Curiosity in. Clarity out.”

---
Questions or tweaks? Update `index.html` sections or ask your assistant for an expanded layout with case studies, services, or blog.
