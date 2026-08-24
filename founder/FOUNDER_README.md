# inkmotion.art/founder — Portfolio Page

## Purpose
A personal portfolio page for Aaron Johnson, accessible at `inkmotion.art/founder`. This page is **not linked from the main inkmotion.art homepage** — it is shared only in job applications and similar contexts. The URL itself is intentional: it signals to hiring managers that the candidate is the founder of an AI video company.

---

## File Structure

```
founder/
├── index.html          ← the portfolio page (served at inkmotion.art/founder)
└── documents/
    ├── ID_Storyboard.pdf
    ├── Needs_Analysis.pdf
    ├── Outline.pdf
    ├── Stabilization.pdf
    ├── M2L1_Activity-2_demo_.pdf
    ├── M2L3_Activities.pdf
    ├── M2L3_Checklist.pdf
    ├── M3L1_Activity-2_demo_.pdf
    └── M7L1_Activity-1_demo_.pdf (removed from page display but kept in repo)
```

The `founder` folder lives in the repo root alongside the main `index.html` (the inkmotion.art homepage). GitHub Pages automatically serves `founder/index.html` at `inkmotion.art/founder` — no additional config needed.

---

## Page Sections

### Header
- Name: Aaron Johnson
- Sub-header: "Portfolio" (single word, Syne font, matches site visual style)
- Contact: aaron@engagingcourses.com (email only — no phone number, to prevent scraping)

### Section 1 — Engaging Courses Academy
- Intro text describing the business
- Embedded YouTube playlist (30 videos): `https://www.youtube.com/playlist?list=PLPwCKY8yByQSi0c8Pv369x6ntpaC148xI`
- 4 selected training workbooks displayed as compact cards (open PDF in new tab):
  - M2L1 — Embrace Word Salad
  - M2L3 — 3CPO Checklist
  - M2L3 — Engaging Layouts Activities
  - M3L1 — Show Don't Tell, Story Replacement
  - *(M7L1 was removed from display — 5 cards looked awkward with 4+1 layout)*

### Section 2 — F5 Instructor-Led Training
- Intro text about Xyleme / Madcap Xyleme authoring tool
- Bulleted list describing each of the 3 course links
- Italicized note: rendering issues in the Xyleme-hosted files are expected and not a content problem
- 3 outbound links (open in new tab):
  - Instructor Guide: `https://dazmuth.github.io/ig/`
  - Presentation: `https://dazmuth.github.io/presentation/`
  - Student Guide: `https://dazmuth.github.io/studentguide/`
- **Xyleme Project Files** subsection — 4 YouTube videos in a 2×2 grid:
  - Storyboard: `https://youtu.be/3H0n7aVY5k8`
  - Outline/Scope: `https://youtu.be/bqc9ZAH6J-Q`
  - Execution: `https://youtu.be/p0TBVJdTLgY`
  - Design: `https://youtu.be/gspktp0532A`

### Section 3 — Nordstrom Agile/Jira Training Program
- Intro text explaining the Nordstrom origin and reuse across other projects
- 4 inline embedded PDF viewers (650px height):
  - ID Storyboard
  - Needs Analysis
  - Outline
  - Stabilization
- Note: these docs reference "Evergreen" (an anonymized client name used in the original documents)

### Footer
- Name + email only

---

## Design
- Matches inkmotion.art visual identity: Syne + DM Sans fonts, warm paper/ink palette, terracotta accent (#d94f2b)
- Single scrollable page, no sub-pages
- Nav links: Engaging Courses Academy / F5 / Nordstrom / Contact (email)
- Fully responsive — mobile collapses nav, video grid stacks to single column

---

## PDF Notes

### Metadata
All 9 PDFs have had their internal Title and Author metadata set (using pikepdf) so browser tabs show clean names instead of "Untitled". Titles follow the pattern: `Document Name — Section/Company`.

### ID_Storyboard.pdf compression
The original file was 18.6MB (scanned at 5100×6600px per page). It was resampled to 150 DPI and recompressed at JPEG quality 70, reducing it to 1.7MB with no meaningful quality loss for screen viewing. The compressed version is what lives in this repo.

### Pre-production docs (Nordstrom section)
The Needs Analysis, Outline, and Stabilization documents reference "Evergreen" — this is the original anonymized client name from the instructional design course scenario. The Nordstrom section intro copy acknowledges that these docs were originally developed at Nordstrom and later reused for other projects.

---

## How to Update

### Change contact email
Search `index.html` for `aaron@engagingcourses.com` — appears in 3 places: nav Contact link, header contact, footer.

### Add/swap a YouTube video (ECA playlist or Xyleme section)
Find the relevant `<iframe src="https://www.youtube.com/embed/VIDEO_ID">` tag and replace `VIDEO_ID` with the new YouTube video ID (the part after `?v=` or after `youtu.be/`).

### Add a workbook card (ECA section)
Copy an existing `<a class="workbook-card">` block, update the `href` to point to the new PDF in `documents/`, and update the tag, title, and open link text.

### Add a new PDF (any section)
1. Upload the PDF to the `documents/` folder in this repo
2. (Optional but recommended) set the PDF's Title metadata using pikepdf before uploading so the browser tab shows a clean name
3. Add an `<iframe src="documents/FILENAME.pdf">` block (for embedded viewer) or an `<a href="documents/FILENAME.pdf" target="_blank">` card (for card link)

---

## Build History
All design decisions, technical choices, and iterative edits for this page were made in the **"AI Businesses" project** in Claude.ai, within the chat titled **"inkmotion.art website"**. If this page needs to be rebuilt from scratch, paste the full conversation history or summarize this README to Claude to restore context.

---

## Contact
Aaron Johnson — aaron@engagingcourses.com
