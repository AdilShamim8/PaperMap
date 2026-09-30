# PaperMap — Paper Section Guide & Contribution System

This document explains everything about PaperMap's **Paper Section**: what it is, how the 20 papers are organized into a curriculum, and exactly how to add or update a paper explainer so it stays consistent with the library. Read it once, top to bottom, before opening your first pull request.

---

## 1. What the Paper Section Is

The Paper Section is the heart of PaperMap: a growing collection of **interactive, research-accurate explainers for landmark AI papers**. Each paper is a single, self-contained HTML file (no frameworks, no build step, no dependencies) that turns a dense research paper into a visual learning experience with:

- **Interactive demos** you can click, toggle, and step through
- **Architecture breakdowns** grounded in the original paper
- **Formula cards** with plain-language piece-by-piece explanations
- **Benchmark tables and animated result charts**
- A **5-question quiz** with explanations
- A **Key Takeaways** reference section

The library currently contains **20 papers organized into 7 learning tracks** — a guided path from the original 2017 Transformer to modern open reasoning models.

## 2. How Papers Are Organized

The curriculum is ordered so each track builds on the last. Papers are grouped by theme, and within a track they follow a rough chronology.

| Track | Theme | Papers |
|---|---|---|
| **I** | Transformer → Modern Language Models | Attention Is All You Need (2017) · BERT (2018) · GPT-2 (2019) · GPT-3 (2020) · T5 (2020) |
| **II** | Scaling + Training | Scaling Laws (2020) · Chinchilla (2022) — *study these two together* |
| **III** | Knowledge + Adaptation | RAG (2020) · LoRA (2021) · ColBERTv2 (2022) |
| **IV** | Instruction + Alignment | InstructGPT / RLHF (2022) · DPO (2023) |
| **V** | In-Context Learning + Reasoning | Chain-of-Thought (2022) · Self-Consistency (2022) · Induction Heads (2022) |
| **VI** | Agents + Tools | ReAct (2022) · Toolformer (2023) |
| **VII** | Open Models + Evaluation | LLaMA (2023) · LLM-as-a-Judge (2023) · DeepSeek-R1 (2025) |

**On the homepage**, the Paper Library section renders: a quick-navigation chip row for the 7 tracks, a curriculum overview map, and one subsection per track containing its paper cards. When you add a paper, it must be placed in the correct track — never appended to the end of the grid.

**Study-pair rule.** Some papers are explicitly designed to be read together (Scaling Laws → Chinchilla). If your paper corrects, extends, or directly follows another paper, cross-link both explainers in the body and footer.

## 3. The Standard Paper Page Structure

Every paper page lives in `paper/` and follows the same skeleton. **Use an existing page (e.g., `paper/BERT.html`) as your template** — copy its `<style>` block verbatim and reuse its utility scripts. Do not redesign the page.

### 3.1 Head metadata (required, every page)

```
<title>{Paper Short Title} — Interactive Guide</title>
<meta name="description">         one specific sentence, mentions interactivity
<meta name="keywords">            paper-specific terms
<meta name="author" content="PaperMap">
<meta name="robots" content="index, follow">
<meta name="theme-color" content="#f59e0b">
<link rel="canonical" href="https://papermap.vercel.app/paper/{FILENAME}.html">
favicon: ../assets/favicon.svg
Open Graph tags (title, description, type, url, site_name, image)
Twitter card tags (summary_large_image + title/description/image)
Google Fonts link (IBM Plex Mono + Instrument Serif + DM Sans)
```

### 3.2 Body skeleton (in order)

1. **Skip link** → `#problem` (or first content section)
2. **Reading progress bar** (fixed, amber)
3. **Nav** — `papermap` logo → `../index.html`, 6–9 section links, a **venue/year badge** (e.g., `NeurIPS 2022`), mobile toggle
4. **Mobile menu** — same links
5. **Hero** — eyebrow ("Interactive Paper Explainer"), serif title with one `<em>` accent, subtitle, two actions (`Start Learning` → first section, `Read the Paper ↗` → arXiv), and **exactly 4 stat blocks**
6. **History section** — a timeline (`tl-item`s) of 4–6 predecessor milestones + a "Key Insight" card
7. **Chapter sections** — `Chapter 01` problem framing with a **bad/good comparison grid**, then 3–5 method/architecture/result chapters:
   - `section-tag` (e.g., `Chapter 02`), `section-title` with `<em>`, `section-desc`
   - `formula-card` for key equations, with `formula-breakdown` pieces explaining each symbol
   - **2–3 interactive demo cards** (see §5)
   - `results-grid` with `result-card`s and animated bars; `comp-table` for system comparisons
   - `problem-list`, `notice-grid`/`notice-card`, `two-col`, `card-sm` stat grids as needed
8. **Impact / Legacy section** — 5–6 `notice-card`s on what followed from the paper
9. **Quiz section** — exactly **5 questions**, 4 options each, with an `explain` line for every question
10. **Key Takeaways** — 6 `card-sm` statements starting with ✅
11. **Footer** — paper citation link, repo link, 3 related-guide links, contact + social strip (copy the social strip HTML verbatim from an existing page)

### 3.3 Utility scripts (copy verbatim, adjust only the ids array)

Every page ends with one `<script>` block containing: smooth-scroll utils, mobile menu toggle, **NAV ACTIVE** section tracking, scroll-reveal (IntersectionObserver), your demo code (IIFEs), the `QUIZ_DATA` array, and the quiz renderer + `answerQuiz` handler. Copy these from `paper/BERT.html` exactly.

> ⚠️ **Known typo trap**: the NAV ACTIVE line must end with `...==='#'+cur));});})();` (double closing paren). If your demos don't initialize, this line is the first thing to check.

## 4. File Naming & Linking Conventions

- **Filenames**: uppercase-friendly, underscore-separated, no spaces — e.g., `BERT.html`, `GPT_2.html`, `Scaling_Laws.html`, `Chain_Of_Thought_Prompting.html`. Spaces in filenames force `%20` URL encoding; never introduce them.
- **Legacy redirects**: two older space-named URLs (RAG, LoRA) are preserved as HTML meta-refresh redirect stubs so old links don't break. Don't delete them; don't create new ones.
- **Internal links**: paper pages link to siblings with `./<Filename>.html`; the homepage and `404.html` use `./paper/<Filename>.html`.
- **Every new paper must be linked from**: the homepage track grid, the homepage footer links, the paper pages it is most related to (2–3 "Related Guides"), and `sitemap.xml`.

## 5. Interactive Demo Rules

Demos are what make a PaperMap page a PaperMap page.

1. Every page needs **at least 2–3 interactive elements**, each with real controls (buttons, tabs, sliders) that change rendered content.
2. Build them as **self-contained IIFEs** rendering into container `<div>`s — no external libraries, no frameworks, no network calls.
3. Prefer the **flex-bar chart pattern** (see any existing page) over canvas; guard every demo with `if(!el)return;`.
4. Data in demos may be precomputed/illustrative, but **numbers you present as paper results must be accurate** — mark approximations with `~`.
5. Demos must work on mobile (test at 390px width) and respect `prefers-reduced-motion`.

## 6. Design / Style Rules (non-negotiable)

The design system is shared across all pages. **Do not restyle, extend, or "improve" it.**

| Token | Value |
|---|---|
| Primary accent (amber) | `#f59e0b` (dim: `rgba(245,158,11,0.12)`) |
| Secondary accents | blue `#3b82f6`, teal `#14b8a6`, green `#22c55e`, purple `#a855f7`, red `#ef4444` |
| Text | `#0f172a` / `#475569` / `#64748b` (3 levels) |
| Backgrounds | `#ffffff`, `#f8fafc`, `#f1f5f9`, `#e2e8f0` |
| Fonts | IBM Plex Mono (mono/labels), Instrument Serif (headings, with `<em>` amber), DM Sans (body) |
| Radii | 10px (`--radius`), 16px (`--radius-lg`) |
| Layout | 1100px max width, 5rem section padding, dividers between sections |

Component rules:
- The `<style>` block is **copied verbatim** from an existing page — paper-specific styling is done with inline styles on existing classes.
- Paper cards on the homepage cycle the five color classes (`amber`, `blue`, `teal`, `purple`, `green`) within their track; the top 3px colored border is set by the class.
- Icons are used sparingly (one per `problem-card`, `feature-card`, or `notice-card`).
- Accessibility: semantic HTML, ARIA labels on icon links, skip links, `prefers-reduced-motion` support, ≥44px touch targets on mobile.

## 7. Content Quality Rules

1. **Research-accurate**: every number, model size, and benchmark score must come from the original paper (or be marked `~` approximate). When unsure, state it qualitatively — never invent a number.
2. **Honest results sections**: say what the paper did NOT solve too (e.g., GPT-2 was far from SOTA on translation; ReAct alone underperforms CoT on some QA).
3. **Beginner-friendly**: explain jargon on first use; use analogies in "Key Insight" cards.
4. **English**, concise sentences, ~600–950 lines of HTML per page.
5. Credit the original authors — explainers are educational derivatives; the footer always cites the paper and links to it.

## 8. Step-by-Step: Adding a New Paper

1. **Pick the paper and its track.** Check the homepage and this file to make sure it's not already covered.
2. **Read the original paper** (arXiv link required). Note: core idea, key numbers, results tables, limitations.
3. **Copy** `paper/BERT.html` as your starting template. Rename it to the underscore convention.
4. **Rewrite** the head metadata, nav links + venue badge, hero (title + 4 stats), and all section content per §3. Keep the `<style>` block and utility scripts untouched.
5. **Build 2–3 interactive demos** per §5 and **5 quiz questions**.
6. **Register the page**:
   - Homepage: add a paper card in the correct track's grid (matching card color cycle), and a footer link.
   - `sitemap.xml`: add the URL.
   - Related paper pages: add a footer "Related Guide" link where natural.
   - Update the roadmap section if your paper starts a new theme.
   - Update the "Papers Live" count in the nav badge and hero stats.
7. **Verify** (see §9), then open a pull request.

## 9. Verification Checklist (run before every PR)

```bash
# 1. Serve locally
python3 -m http.server 8080

# 2. Syntax-check the page's JavaScript
python3 -c "
import re
html = open('paper/YOUR_PAGE.html').read()
m = re.findall(r'<script>(.*?)</script>', html, re.S)
open('/tmp/check.js','w').write(m[-1])
" && node --check /tmp/check.js

# 3. Structure checks
# - exactly one </body>, one </html>, one <script>
# - every nav link id exists as a <section id=...> AND appears in the NAV ACTIVE ids array
# - all ./paper/*.html links resolve (no %20, no 404s)
# - quizContainer renders 5 quiz cards; demos initialize
```

Then in a browser: click every demo control, answer one quiz question, resize to 390px, and check the console for errors. Zero errors is the bar.

## 10. Pull Request Checklist

- [ ] Paper file added inside `paper/` with correct underscore naming
- [ ] Full head metadata (title, description, canonical, OG, Twitter)
- [ ] `<style>` block and utility scripts copied verbatim (only the NAV ACTIVE ids array changed)
- [ ] 2–3 working interactive demos + 5-question quiz with explanations
- [ ] Homepage card added **in the correct track**, footer link added, "Papers Live" count updated
- [ ] `sitemap.xml` updated
- [ ] Related-guide cross-links added on 2–3 sibling paper pages
- [ ] All links tested locally (no 404s, no `%20` URLs)
- [ ] Desktop (1440px) and mobile (390px) layout checked
- [ ] Zero console errors; `node --check` passes
- [ ] Numbers are research-accurate (or explicitly marked `~`)

## 11. Using AI to Draft a Paper Page

PaperMap pages can be drafted with an AI assistant, then reviewed and polished by a human. The original guided workflow lives in this Google Doc: https://docs.google.com/document/d/1PYVkWYqFDUZ6bY1hyAk7zOauGnyIIWjDh44S918wOCM/edit?usp=sharing

When using AI (Claude, GPT, etc.), paste it this file plus your paper details (title, authors, venue, year, arXiv link, key results), and ask it to produce a page that follows **this** document's rules — BERT.html as the structural template, verbatim style block, the exact demo and quiz patterns. Then run the §9 checklist yourself: AI output must be verified line-by-line for number accuracy and link correctness before it can be merged.

---

**Questions or ideas for new papers?** Open a GitHub issue or pull request at https://github.com/AdilShamim8/PaperMap — contributions that follow this guide get merged fast.
