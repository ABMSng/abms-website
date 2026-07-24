# Site Project — Setup Guide

## 1. Install & preview locally
```
npm install
npm run serve
```
Visit http://localhost:8080

## 2. Push to GitHub
```
git init
git add .
git commit -m "Initial site"
```
Create a new repo on GitHub, then:
```
git remote add origin YOUR_REPO_URL
git push -u origin main
```

## 3. Deploy on Netlify
1. Go to netlify.com → "Add new site" → "Import an existing project" → connect GitHub → pick this repo.
2. Build command: `npm run build`
3. Publish directory: `_site`
4. Deploy.

## 4. Enable content editing (Decap CMS)
1. In the Netlify dashboard: **Site settings → Identity → Enable Identity**.
2. Under Identity settings, enable **Git Gateway**.
3. Under Identity → Registration, set to **Invite only** (so random people can't sign up).
4. Invite your client's email as a user (Identity tab → Invite users).
5. Client visits `yourdomain.com/admin/`, accepts the invite, sets a password, and can log in to edit content.

## 5. Point your Cloudflare domain to Netlify
1. In Netlify, find the site's default `.netlify.app` URL and the custom domain instructions (Site settings → Domain management → Add custom domain).
2. In Cloudflare DNS for your domain, add the CNAME/A records Netlify gives you (Netlify shows the exact values to enter).
3. SSL activates automatically once DNS propagates (usually within an hour).

## Site structure
- `src/index.md` — Home
- `src/about/index.md` — About Us (Mission & Vision, Focus, Activities, Expected Outcomes as sections)
- `src/leadership/index.md` — Leadership (Management, Advisory Council)
- `src/thematic-areas/index.md` — Thematic Areas
- `src/programs/index.md` — Programs
- `src/newsletter/index.njk` — Newsletter & Opportunity (auto-lists posts)
- `src/newsletter-posts/*.md` — individual newsletter/opportunity posts (client can add new ones from the CMS)
- `src/contact/index.md` — Contact
- `src/admin/` — Decap CMS editor (client logs in at `/admin/`)

## Notes
- All page text is edited through markdown files or the `/admin/` CMS — no page needs raw HTML edits.
- To add a new static page later, duplicate a folder like `src/programs/` and add it to `src/_includes/base.njk` nav and `src/admin/config.yml`.
