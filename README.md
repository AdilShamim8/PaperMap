# PaperMap

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Static HTML](https://img.shields.io/badge/HTML-100%25-blue)](https://github.com/AdilShamim8/PaperMap)
[![Papers](https://img.shields.io/badge/Papers-20-FF6B6B)](https://papermap.vercel.app/)
[![Tracks](https://img.shields.io/badge/Learning_Tracks-7-14b8a6)](https://papermap.vercel.app/#library)

PaperMap is an open-source, static-first library of interactive AI paper explainers.

The goal is simple: turn dense research papers into visually rich, beginner-friendly, and research-accurate learning experiences.

Current status: **20 live interactive paper explainers**, organized into a **7-track curriculum** — from the original Transformer to DeepSeek-R1.

## Live Library

- [Homepage](https://papermap.vercel.app/)

### Track I — Transformer → Modern Language Models
- [Attention Is All You Need](https://papermap.vercel.app/paper/Attention_Is_All_You_Need.html) · 2017
- [BERT: Pre-training of Deep Bidirectional Transformers](https://papermap.vercel.app/paper/BERT.html) · 2018
- [Language Models are Unsupervised Multitask Learners (GPT-2)](https://papermap.vercel.app/paper/GPT_2.html) · 2019
- [Language Models are Few-Shot Learners (GPT-3)](https://papermap.vercel.app/paper/Language_Models_are_Few_Shot_Learners.html) · 2020
- [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer (T5)](https://papermap.vercel.app/paper/T5.html) · 2020

### Track II — Scaling + Training
- [Scaling Laws for Neural Language Models](https://papermap.vercel.app/paper/Scaling_Laws.html) · 2020
- [Training Compute-Optimal Large Language Models (Chinchilla)](https://papermap.vercel.app/paper/Chinchilla.html) · 2022

> Study tip: read Scaling Laws and Chinchilla **together** — the second paper corrects the first.

### Track III — Knowledge + Adaptation
- [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks (RAG)](https://papermap.vercel.app/paper/RAG_Retrieval_Augmented_Generation.html) · 2020
- [LoRA: Low-Rank Adaptation of Large Language Models](https://papermap.vercel.app/paper/LoRA_Low_Rank_Adaptation.html) · 2021
- [ColBERTv2: Effective and Efficient Retrieval](https://papermap.vercel.app/paper/ColBERTv2.html) · 2022

### Track IV — Instruction + Alignment
- [Training Language Models to Follow Instructions with Human Feedback (InstructGPT)](https://papermap.vercel.app/paper/Training_Language_Models_to_Follow_Instructions_with_Human_Feedback.html) · 2022
- [Direct Preference Optimization (DPO)](https://papermap.vercel.app/paper/DPO.html) · 2023

### Track V — In-Context Learning + Reasoning
- [Chain-of-Thought Prompting Elicits Reasoning in LLMs](https://papermap.vercel.app/paper/Chain_Of_Thought_Prompting.html) · 2022
- [Self-Consistency Improves Chain of Thought Reasoning](https://papermap.vercel.app/paper/Self_Consistency.html) · 2022
- [In-context Learning and Induction Heads](https://papermap.vercel.app/paper/Induction_Heads.html) · 2022

### Track VI — Agents + Tools
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://papermap.vercel.app/paper/ReAct.html) · 2022
- [Toolformer: Language Models Can Teach Themselves to Use Tools](https://papermap.vercel.app/paper/Toolformer.html) · 2023

### Track VII — Open Models + Evaluation
- [LLaMA: Open and Efficient Foundation Language Models](https://papermap.vercel.app/paper/LLaMA.html) · 2023
- [Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena](https://papermap.vercel.app/paper/LLM_as_a_Judge.html) · 2023
- [DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via RL](https://papermap.vercel.app/paper/DeepSeek_R1.html) · 2025

## Why PaperMap

- Interactive explanations instead of static summaries
- Research-accurate content grounded in original papers
- Shared visual language across all paper pages
- A structured curriculum — not a random pile of papers
- Pure HTML, CSS, and JavaScript with no framework overhead
- Easy to contribute and easy to deploy

## Tech Stack

- HTML
- CSS
- Vanilla JavaScript
- Static hosting (Vercel, Netlify, GitHub Pages, Cloudflare Pages)

## Project Structure

```text
PaperMap/
|- index.html                  (homepage: 7-track curriculum library)
|- 404.html
|- PROMPT.md                   (paper section guide + contribution system)
|- assets/
|  |- favicon.svg
|- paper/
|  |- Attention_Is_All_You_Need.html
|  |- BERT.html
|  |- GPT_2.html
|  |- Language_Models_are_Few_Shot_Learners.html
|  |- T5.html
|  |- Scaling_Laws.html
|  |- Chinchilla.html
|  |- RAG_Retrieval_Augmented_Generation.html
|  |- LoRA_Low_Rank_Adaptation.html
|  |- ColBERTv2.html
|  |- Training_Language_Models_to_Follow_Instructions_with_Human_Feedback.html
|  |- DPO.html
|  |- Chain_Of_Thought_Prompting.html
|  |- Self_Consistency.html
|  |- Induction_Heads.html
|  |- ReAct.html
|  |- Toolformer.html
|  |- LLaMA.html
|  |- LLM_as_a_Judge.html
|  |- DeepSeek_R1.html
|  |- Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.html   (legacy redirect)
|  |- LoRA Low-Rank Adaptation of Large Language Models.html                 (legacy redirect)
|- robots.txt
|- sitemap.xml
|- LICENSE
|- README.md
```

## Run Locally

Option 1:

Open index.html directly in your browser.

Option 2 (recommended):

```bash
# Python
python -m http.server 8080

# Node.js
npx serve
```

Then open http://localhost:8080

## How the Paper Section Works

The Paper Section is a curriculum of 20 papers organized into 7 tracks (Transformers → LLMs → Scaling → Retrieval/Adaptation → Alignment → Reasoning → Agents → Open Models/Evaluation). Every explainer follows one shared page template, one design system, and one contribution workflow.

**Before adding or updating a paper, read [PROMPT.md](PROMPT.md).** It is the complete, contributor-friendly guide to the Paper Section: how papers are organized, the required page structure, naming and linking conventions, design/style rules, interactive demo requirements, verification steps, and the pull request checklist.

## Add a New Paper (Standard Workflow)

1. Read [PROMPT.md](PROMPT.md) completely.
2. Create a new HTML file inside `paper/` using underscore naming (for example `BERT.html`).
3. Use an existing paper page (e.g., `paper/BERT.html`) as your style and structure template — copy the `<style>` block verbatim.
4. Keep the content research-accurate, include 2–3 interactive demos and a 5-question quiz.
5. Add your paper card to the correct track in `index.html`, update the footer links and paper count.
6. Add the URL to `sitemap.xml` and cross-link 2–3 related guides.
7. Verify responsive behavior on desktop and mobile, and run the checks in PROMPT.md §9.
8. Include complete metadata in the head section.

## Contributing

Users and developers are welcome to contribute to this open-source project.

If you want an easy, guided process, use the workflow below.

## Easy Contribution Workflow (Using Prompt + Claude)

1. Read the contribution guide: [PROMPT.md](PROMPT.md) in this repository.
   (The original guided prompt template also lives here:
   https://docs.google.com/document/d/1PYVkWYqFDUZ6bY1hyAk7zOauGnyIIWjDh44S918wOCM/edit?usp=sharing)
2. Go to Claude AI:
   https://claude.ai
3. Paste PROMPT.md plus your paper details: paper name, official publication link, and PDF link (recommended).
4. Ask Claude to generate a complete HTML explainer following PROMPT.md's rules.
5. Download the generated HTML file.
6. Fork this GitHub repository.
7. Upload your HTML file into the `paper/` folder.
8. Update `index.html` so your paper appears on the homepage in the correct track.
9. Verify the page with PROMPT.md's checklist (§9) — fix any console errors or broken links.
10. Open a Pull Request.

Congratulations, you are now part of the PaperMap community.

## Pull Request Checklist

1. Paper file added inside `paper/` with underscore naming.
2. Homepage card added in the correct track, footer links and paper count updated.
3. Links tested locally (no 404s, no `%20` URLs).
4. Desktop and mobile layout checked.
5. Metadata updated (title, description, canonical, social tags).
6. `sitemap.xml` updated.
7. Interactive demos and quiz verified working.
8. `node --check` passes on the page script (see PROMPT.md §9).

## Attribution

All explainers are educational derivatives of original research papers.
Credit always belongs to the original authors.

## License

This project is licensed under the [MIT License](LICENSE).

## Connect With Me
<p align="center">
  <a href="https://www.adilshamim.me/">
    <img src="https://img.shields.io/badge/Website-000000?style=for-the-badge&logo=About.me&logoColor=white" />
  </a>
  <a href="https://adilshamim8.medium.com/">
    <img src="https://img.shields.io/badge/Medium-12100E?style=for-the-badge&logo=medium&logoColor=white" />
  </a>
  <a href="https://linkedin.com/in/adilshamim8">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="https://twitter.com/adil_shamim8">
    <img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" />
  </a>
  <a href="https://www.kaggle.com/adilshamim8">
    <img src="https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white" />
  </a>
  <a href="https://leetcode.com/u/AdilShamim8">
    <img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" />
  </a>
</p>

<p align="center">
</p>
