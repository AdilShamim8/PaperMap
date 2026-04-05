# PaperMap — Interactive Research Paper Library

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Static HTML](https://img.shields.io/badge/HTML-100%25-blue)](https://github.com/AdilShamim8/PaperMap)
[![Live](https://img.shields.io/badge/%F0%9F%8C%90-Live_Demo-FF6B6B)](https://papermap.vercel.app/)

**From dense research papers to interactive, visual learning experiences.**

PaperMap transforms landmark AI papers into beautiful, self-contained interactive explainers. Each paper becomes a rich, production-quality educational page featuring animations, live demos, architectural visualizations, and quizzes — all while maintaining a consistent, polished design system.

### Live Explainers
- **[Attention Is All You Need](https://papermap.vercel.app/Attention_Is_All_You_Need.html)** — The Transformer architecture (Vaswani et al., 2017)
- **[Language Models are Few-Shot Learners](https://papermap.vercel.app/Language_Models_are_Few_Shot_Learners.html)** — GPT-3 and in-context learning (Brown et al., 2020)
- **[Training Language Models to Follow Instructions with Human Feedback](https://papermap.vercel.app/Training_Language_Models_to_Follow_Instructions_with_Human_Feedback.html)** — RLHF & InstructGPT (Ouyang et al., 2022)

**[Explore the full library →](https://papermap.vercel.app/)**

---

## ✨ Features

- **Highly Interactive** — Token playgrounds, attention visualizations, training pipeline animations, and more
- **Research-Accurate** — Content is grounded in the original papers with clear references
- **Static-First** — Pure HTML, CSS, and vanilla JavaScript. No build step, no frameworks, no dependencies
- **Consistent Design System** — All explainers share the same high-quality UI components and visual language
- **Mobile-First & Accessible** — Responsive design, keyboard navigation, ARIA labels, and reduced motion support
- **Easily Extensible** — Add new papers while preserving one unified homepage and style

## Why PaperMap?

Most research papers are difficult to digest. PaperMap bridges the gap between academic writing and deep understanding by turning theory into interactive products.

## Project Structure

```bash
PaperMap/
├── index.html                                      # Homepage + paper catalog
├── Attention_Is_All_You_Need.html                  # Interactive explainer
├── Language_Models_are_Few_Shot_Learners.html
├── Training_Language_Models_to_Follow_Instructions_with_Human_Feedback.html
├── favicon.svg
├── LICENSE
└── README.md
```

## How to Add a New Paper

1. **Create a new HTML file** using clear `Pascal_Case.html` naming (e.g. `BERT.html` or `Diffusion_Models.html`)
2. **Use an existing explainer as a template** to maintain visual and structural consistency
3. **Add a new card** in `index.html` under the Paper Library section
4. **Include proper metadata** in the `<head>` (title, description, Open Graph tags)
5. **Test thoroughly** on both desktop and mobile

The architecture is deliberately simple so contributors can focus on creating excellent educational content rather than fighting with tooling.

## Local Development

**Option 1 (Simplest):** Just open `index.html` in your browser.

**Option 2 (Recommended):**
```bash
# Python
python -m http.server 8080

# Node.js
npx serve
```

Then visit `http://localhost:8080`

## Deployment

This project works on any static hosting platform:

- **Vercel** (current live site)
- **Netlify**
- **GitHub Pages**
- **Cloudflare Pages**

For GitHub Pages: Settings → Pages → Deploy from `main` branch (root folder).

## Roadmap

- More foundational papers (BERT, ViTs, Diffusion Models, RAG, etc.)
- Search & filtering on the homepage
- Difficulty ratings and estimated reading time
- Expanded interactive components and quizzes
- Dark mode support

## Attribution

All explainers are educational derivatives of the original research papers. We greatly respect the work of the original authors.

**Current papers:**
- "Attention Is All You Need" — Ashish Vaswani, Noam Shazeer, et al.
- "Language Models are Few-Shot Learners" — Tom Brown, Benjamin Mann, et al.
- "Training Language Models to Follow Instructions with Human Feedback" — Long Ouyang, Jeffrey Wu, et al.

## License

This project is open-sourced under the [MIT License](LICENSE).

---

*Built for the AI research and education community.*
```
