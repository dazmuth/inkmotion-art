# INKMOTION_WEBSITE.md — inkmotion.art Website Documentation

> **This is a living document.** Update it whenever a significant decision is made about the website — hosting, DNS, forms, structure, or Stage 2 planning.
>
> Companion documents in the Inkmotion project:
> - `INKMOTION_TECHNICAL.md` — app architecture, APIs, code
> - `INKMOTION_STRATEGY.md` — pitch, market, investors, business decisions
> - `INKMOTION_STATUS.md` — current state and immediate next steps
> - `INKMOTION_WEBSITE.md` — this file (website only)

---

## Domain

- **Domain:** inkmotion.art
- **Registrar:** GoDaddy
- **Registration:** 3-year prepaid (~$80), purchased 2025
- **DNS management:** GoDaddy (DNS records managed directly in GoDaddy dashboard)

---

## Hosting

- **Host:** GitHub Pages (free tier)
- **Repo:** github.com/dazmuth/inkmotion-art (public)
- **Branch:** main
- **Deploy:** automatic on push to main

### Why GitHub Pages over alternatives
- Netlify was considered but its credit-based free tier could take the site offline mid-month if limits hit
- Cloudflare Pages was considered — marginally better than GitHub Pages but not enough to justify a new account
- GitHub Pages chosen because: already in use for other projects (dazmuth.github.io), unlimited static site deploys, clean custom domain support, zero ongoing cost

---

## DNS Configuration (GoDaddy)

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A | @ | 185.199.108.153 | 1 Hour |
| A | @ | 185.199.109.153 | 1 Hour |
| A | @ | 185.199.110.153 | 1 Hour |
| A | @ | 185.199.111.153 | 1 Hour |
| CNAME | www | dazmuth.github.io | 30 min |
| TXT | _github-pages-challenge-dazmuth | 557d98eb4c9d5fea5cc1c2f99df25f | 1 Hour |

**HTTPS:** Enabled via GitHub Pages (Let's Encrypt, auto-provisioned). The "Enforce HTTPS" checkbox in GitHub Pages settings is enabled.

**Common issue:** If you ever re-add a GoDaddy parking A record (e.g. "website under construction"), it will conflict with the GitHub A records and break SSL cert provisioning. Only the 4 GitHub A records above should point to @.

---

## File Structure

```
inkmotion-art/ (repo root)
├── index.html              ← inkmotion.art homepage (Stage 1 landing page)
├── INKMOTION_WEBSITE.md    ← this file
├── README.md               ← GitHub repo readme
└── founder/
    ├── index.html          ← inkmotion.art/founder (portfolio page, unlisted)
    ├── FOUNDER_README.md   ← documentation for the founder page
    └── documents/
        └── *.pdf           ← portfolio PDFs
```

---

## Email Capture (Formspree)

- **Provider:** Formspree (free tier)
- **Endpoint:** `https://formspree.io/f/xvzynkqe`
- **Account email:** dazmuth@proton.me
- **Form location:** bottom of inkmotion.art homepage
- **Fields captured:** Name, Email, Interest type (customer / engineer / investor / other)
- **Where submissions go:** Formspree dashboard (dashboard.formspree.io)
- **Email notifications:** NOT active on free tier — check dashboard manually
- **Upgrade trigger:** upgrade to Formspree paid plan when actively advertising the product and need email notifications redirected to dazmuth@proton.me

---

## inkmotion.art Homepage (Stage 1)

### Purpose
Landing page for investors, engineers, and potential customers. Drives email capture via Formspree form. Not a product — a pitch and a signal.

### Sections
1. **Hero** — tagline, two CTAs (See the demo / Express interest)
2. **Problem strip** — 4-card dark section explaining the gap in current AI video tools
3. **How it works** — 4-step process (upload scene → upload references → give instructions → generate)
4. **Demos** — YouTube video embeds (placeholder cards until real demo videos are added)
5. **Interest form** — Name, email, interest type, submit
6. **Footer**

### How to add a demo video
Find the placeholder block in `index.html`:
```html
<!-- TO ADD VIDEO: replace the placeholder div below with:
     <iframe src="https://www.youtube.com/embed/YOUR_VIDEO_ID" allowfullscreen></iframe>
-->
```
Replace the placeholder `<div>` with the iframe, swapping `YOUR_VIDEO_ID` for the actual YouTube video ID.

### Visual identity
- **Fonts:** Syne (display/headings) + DM Sans (body)
- **Colors:** Paper #f5f2ee, Ink #0e0e0e, Accent terracotta #d94f2b
- **Style:** warm, editorial, hand-crafted feel — deliberately contrasts with cold tech/SaaS aesthetics

---

## inkmotion.art/founder (Portfolio Page)

Separate page for job applications. Not linked from the main site. See `founder/FOUNDER_README.md` for full documentation.

---

## Stage 1 vs Stage 2

### Stage 1 (current)
- Static HTML, GitHub Pages hosted
- No backend, no payments, no user accounts
- Goal: pitch investors/engineers, capture interest emails, validate the concept publicly
- All content managed by editing HTML files directly and pushing to GitHub

### Stage 2 (post-fundraise)
- Full application hosted here — user login, video generation, payments
- Domain stays inkmotion.art — DNS will be re-pointed to wherever the app is hosted (likely Vercel, Render, AWS, or similar)
- DNS change at that point is the same 10-minute process as the initial setup — just update GoDaddy A records to point to the new host
- Stage 2 build will be handled by a contract developer or employee
- The Stage 1 static site will be retired or archived at that point

---

## Build History & Claude Context

All website design decisions, technical choices, and iterative edits were made in the **"AI Businesses" project** in Claude.ai, within the chat titled **"inkmotion.art website"**. To restore full context for future edits, open that chat or paste this document plus `FOUNDER_README.md` into a new Claude session.

---

## Key Contacts & Credentials

| Item | Value |
|------|-------|
| Domain registrar | GoDaddy (AJ's account) |
| GitHub account | dazmuth |
| Formspree account | dazmuth@proton.me |
| Founder contact | aaron@engagingcourses.com |
| InkMotion contact | dazmuth@proton.me |

---

*Last updated: August 2026*
