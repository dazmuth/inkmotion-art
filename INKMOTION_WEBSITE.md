# INKMOTION_WEBSITE.md — inkmotion.art Website Documentation

> **This is a living document.** Update it whenever a significant decision is made about the website: hosting, DNS, forms, structure, or content direction.
>
> Companion documents in the Inkmotion project:
> - `INKMOTION_TECHNICAL.md` — app architecture, APIs, code (old AI-video product)
> - `INKMOTION_STRATEGY.md` — pitch, market, investors (old AI-video product)
> - `INKMOTION_STATUS.md` — current state and next steps
> - `INKMOTION_WEBSITE.md` — this file (website only)
> - `azmuth-site/README.md` — go-live and maintenance steps for author-page.inkmotion.art

---

## Direction change (November 2026)

The AI-video product is **abandoned**. Kling shipped the same idea (per-character control), so there is nothing left to pitch. inkmotion.art is now about **authorship**: a home for innovative methods for storytellers, plus the writing of John Azmuth (AJ's pen name): novels, screenplays, short writing.

What this retires:
- The investor/engineer pitch page, demo videos, problem strip, and interest-type form.
- Stage 2 (app, payments, contract developer). It no longer applies.
- The old technical and strategy docs now describe a shelved product. Keep them for history only.

---

## Domain

- **Domain:** inkmotion.art
- **Registrar:** GoDaddy
- **Registration:** 3-year prepaid (~$80), purchased 2025
- **DNS management:** GoDaddy dashboard

---

## Site map

| URL | Repo | What it is |
|-----|------|------------|
| inkmotion.art | `dazmuth/inkmotion-art` | Minimal landing page and email signup |
| inkmotion.art/founder | `dazmuth/inkmotion-art` | Portfolio page for job applications (unlisted, not linked) |
| inkmotion.art/image1, /image2 | `dazmuth/inkmotion-art` | Single-image display pages |
| author-page.inkmotion.art | separate repo (e.g. `azmuth-site`) | John Azmuth bio, photo and the *Hole Attic* reader |

---

## Hosting

- **Host:** GitHub Pages (free tier), account `dazmuth`
- **Branch:** main, deploys automatically on push
- **Rule:** GitHub Pages allows **one custom domain per repo**. That is why the Azmuth subdomain needs its own repo.
- **Repos must be public.** Free GitHub plans can't publish Pages from private repos. Even on paid plans, a published Pages site is public.

### Why GitHub Pages over alternatives
- Netlify's credit-based free tier could take the site offline mid-month.
- Cloudflare Pages was marginally better but not worth a new account.
- GitHub Pages: already in use, unlimited static deploys, clean custom domains, zero cost.

---

## DNS Configuration (GoDaddy)

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A | @ | 185.199.108.153 | 1 Hour |
| A | @ | 185.199.109.153 | 1 Hour |
| A | @ | 185.199.110.153 | 1 Hour |
| A | @ | 185.199.111.153 | 1 Hour |
| CNAME | www | dazmuth.github.io | 30 min |
| CNAME | author-page | dazmuth.github.io | 1 Hour |
| TXT | _github-pages-challenge-dazmuth | 557d98eb4c9d5fea5cc1c2f99df25f | 1 Hour |

**HTTPS:** Provided by GitHub Pages (Let's Encrypt, auto). Tick "Enforce HTTPS" once the DNS check passes. Do this for each repo, including the Azmuth one.

**Common issue:** A GoDaddy parking A record ("website under construction") conflicts with the GitHub A records and blocks the HTTPS certificate. Only the 4 GitHub A records should point to @.

The existing TXT verification of inkmotion.art on the GitHub account should cover subdomains.

---

## File Structure

```
inkmotion-art/ (repo root)
├── index.html              ← landing page (replace with inkmotion-home/index.html)
├── INKMOTION_WEBSITE.md    ← this file
├── README.md               ← GitHub repo readme
├── founder/
│   ├── index.html          ← /founder portfolio page (unlisted)
│   ├── FOUNDER_README.md
│   └── documents/*.pdf
├── image1/  (index.html, image.png)
└── image2/  (index.html, image.png)

azmuth-site/ (separate repo, author-page.inkmotion.art)
├── index.html              ← bio, photo, reader, request form, unlock form
├── avatar-blackbar-square.webp   ← photo beside the bio (542 KB)
├── avatar-blackbar-square.png    ← same photo, 3 MB, fallback only
├── README.md
└── books/
    ├── hole-attic-chapter-1.pdf   ← public preview
    └── hole-attic.enc             ← full novel, encrypted

Kept on AJ's computer, NOT in any repo:
├── encrypt-book.html       ← local tool that locks a PDF
└── original full novel PDF
```

---

## Email Capture (Formspree)

- **Provider:** Formspree, free plan
- **Endpoint:** `https://formspree.io/f/xvzynkqe` (one form, used by both sites)
- **Account email:** dazmuth@proton.me
- **Limit:** 50 submissions per month across all forms. Check the dashboard if signups seem to stop.
- **Notifications:** not confirmed active on the free plan. Check the dashboard manually, or add a second notification email in Formspree settings.
- **Spam:** hidden `_gotcha` honeypot field on every form.
- **Telling forms apart:** each form sends a hidden `source` field.

| `source` value | Where it comes from |
|----------------|---------------------|
| `inkmotion-landing` | Signup on inkmotion.art |
| `azmuth-code-request` | "Request a code" on author-page.inkmotion.art (also sends `book=Hole Attic`) |

---

## inkmotion.art Homepage

Deliberately minimal. Three elements:
1. Header: **Inkmotion.Art** (hand-drawn underline that draws in; respects reduced-motion settings)
2. Sentence: "The premier home of innovative methods for 21st century storytellers"
3. Email signup labelled "Sign up to learn more about Inkmotion.Art"

On success the form is replaced by "Thanks. You're on the list."

**Visual identity:** Syne (display) + DM Sans (body). Paper `#f5f2ee`, ink `#0e0e0e`, accent terracotta `#d94f2b`.

**Capitalization (decided Nov 2026):** the headline and signup label both read "Inkmotion.Art". The headline sizes itself to fit any screen width (`--fit` in the CSS is the measured width of the text; re-measure it if the text or font changes).

---

## author-page.inkmotion.art

### Purpose
John Azmuth's writing page: a short bio, then a scrolling PDF reader. Visitors read Chapter 1 of the novel *Hole Attic* for free. They can request a code that unlocks the whole story in the reader and enables PDF download.

### Page flow
1. **Bio and photo:** bio text on the left, photo on the right at the same height under the "John Azmuth" heading (photo moves above the text on phones and small tablets)
2. **Reader:** shows Chapter 1 by default
3. **Request a code:** email form (Formspree, `source=azmuth-code-request`)
4. **Unlock:** reader opens the full novel, and a download link appears (file name `Hole-Attic-John-Azmuth.pdf`)

**Magic link:** `https://author-page.inkmotion.art/?code=XXXX-XXXX-XXXX-XXXX` unlocks with one click. The code is then removed from the address bar and remembered in the reader's browser.

### How the lock works
A static site can't truly hide files, and the repo is public. So the full novel is **encrypted before upload**: AES-256-GCM, key derived from the code with PBKDF2-SHA256 (600,000 iterations). Anyone can download `hole-attic.enc`, but it is unreadable without the code. The reader's browser decrypts it locally. Nothing is sent to a server.

- Codes are 16 characters shown as `XXXX-XXXX-XXXX-XXXX` (about 79 bits). Capitals and dashes don't matter when typing.
- **Never** upload the original PDF to the repo. GitHub keeps deleted files in history.
- Save each code in a password manager. It can't be recovered.

### Sending a reader their code (manual)
1. A request arrives in the Formspree dashboard (source `azmuth-code-request`).
2. Reply from your own email using the template in `azmuth-site/README.md`, including the magic link.

### Known limits
- One code works for everyone. If it leaks, lock the book again with a new code and upload the new `.enc`; the old code stops working and readers with it saved are asked for the new one.
- Pages are drawn as images, so readers can't select or copy text. Chapter 1 is public by design.
- The reader loads pdf.js 3.11.174 from the jsDelivr CDN. If that fails, the page falls back to a link to Chapter 1.
- Formspree free plan: 50 submissions/month total.

---

## TBD list (placeholders waiting on AJ)

AJ left these as placeholders on purpose to review the layout first.

| Item | Where | Status |
|------|-------|--------|
| Real bio | `azmuth-site/index.html`, `<p class="bio">` | Done (Nov 10) |
| Real Chapter 1 PDF | `azmuth-site/books/hole-attic-chapter-1.pdf` (keep file name; set the PDF Title property first) | TBD, currently a 6-page placeholder |
| Real full novel, locked | `azmuth-site/books/hole-attic.enc` | TBD, currently an encrypted 30-page placeholder with a demo code (see the azmuth-site README) |
| Capitalization | homepage | Done: "Inkmotion.Art" |
| Second Formspree notification email | Formspree settings | Optional |
| Update this repo's `README.md` | repo root | TBD |

---

## Go-live checklist

**inkmotion.art (existing repo)**
- [ ] Replace `index.html` with `inkmotion-home/index.html`
- [ ] Commit and push; confirm the live page

**author-page.inkmotion.art (new)**
- [ ] Create a new **public** repo; upload `index.html`, `README.md`, `books/`
- [x] GoDaddy DNS: add CNAME `author-page` → `dazmuth.github.io`
- [ ] Repo Settings → Pages: deploy from `main` / root; custom domain `author-page.inkmotion.art`
- [ ] Wait for the DNS check (up to an hour), then tick **Enforce HTTPS**
- [ ] Test the placeholder code, then swap in the real files (see "Put in the real book" in the azmuth-site README)
- [ ] Submit both forms once and confirm they reach the Formspree dashboard

---

## inkmotion.art/founder (Portfolio Page)

Separate page for job applications. Not linked from the main site. See `founder/FOUNDER_README.md`. Contact: aaron@engagingcourses.com. The phone number is intentionally left off to avoid scraping.

---

## Build History & Claude Context

- **Aug 2026:** Original investor/engineer landing page, /founder portfolio, /image1 and /image2, Formspree wiring. Built in the "AI Businesses" project, chat "inkmotion.art website".
- **Nov 2026:** Pivot to authorship. Homepage rebuilt as a minimal landing page. author-page.inkmotion.art and the encrypted reader created, with a local lock tool. Site went live Nov 10 after HTTPS was enabled (the unlock needs HTTPS).
- **Nov 10, 2026:** Real bio and photo added; "Get a code" button fixed; homepage headline fitted to all screen widths and changed to "Inkmotion.Art".

To restore context, paste this document plus `azmuth-site/README.md` and `FOUNDER_README.md` into a new Claude session.

---

## Key Contacts & Credentials

| Item | Value |
|------|-------|
| Domain registrar | GoDaddy (AJ's account) |
| GitHub account | dazmuth |
| Formspree account | dazmuth@proton.me |
| Founder contact | aaron@engagingcourses.com |
| Site contact | dazmuth@proton.me |

---

*Last updated: November 2026*
