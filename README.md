# PaperMap

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Static HTML](https://img.shields.io/badge/HTML-100%25-blue)](https://github.com/AdilShamim8/PaperMap)
[![Live Demo](https://img.shields.io/badge/Live-Demo-FF6B6B)](https://papermap.vercel.app/)

PaperMap is an open-source, static-first library of interactive AI paper explainers.

The goal is simple: turn dense research papers into visually rich, beginner-friendly, and research-accurate learning experiences.

## Live Library

- [Homepage](https://papermap.vercel.app/)
- [Attention Is All You Need](https://papermap.vercel.app/paper/Attention_Is_All_You_Need.html)
- [Language Models are Few-Shot Learners](https://papermap.vercel.app/paper/Language_Models_are_Few_Shot_Learners.html)
- [Training Language Models to Follow Instructions with Human Feedback](https://papermap.vercel.app/paper/Training_Language_Models_to_Follow_Instructions_with_Human_Feedback.html)
- [Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks](https://papermap.vercel.app/paper/Retrieval-Augmented%20Generation%20for%20Knowledge-Intensive%20NLP%20Tasks.html)

## Why PaperMap

- Interactive explanations instead of static summaries
- Research-accurate content grounded in original papers
- Shared visual language across all paper pages
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
|- index.html
|- 404.html
|- assets/
|  |- favicon.svg
|- paper/
|  |- Attention_Is_All_You_Need.html
|  |- Language_Models_are_Few_Shot_Learners.html
|  |- Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.html
|  |- Training_Language_Models_to_Follow_Instructions_with_Human_Feedback.html
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

## Add a New Paper (Standard Workflow)

1. Create a new HTML file inside paper/.
2. Use an existing paper page as your style and structure template.
3. Keep naming clean and readable, for example BERT.html or Diffusion_Models.html.
4. Add your paper card and links in index.html.
5. Verify responsive behavior on desktop and mobile.
6. Include complete metadata in the head section.

## Contributing

Users and developers are welcome to contribute to this open-source project.

If you want an easy, guided process, use the workflow below.

## Easy Contribution Workflow (Using Prompt + Claude)

1. Open this document and copy the prompt template:
   https://docs.google.com/document/d/1PYVkWYqFDUZ6bY1hyAk7zOauGnyIIWjDh44S918wOCM/edit?usp=sharing
2. Go to Claude AI:
   https://claude.ai
3. Paste the prompt you copied from the document.
4. Provide your paper details: paper name, official publication link, and PDF link (recommended).
5. Ask Claude to generate a complete HTML explainer.
6. Download the generated HTML file.
7. Fork this GitHub repository.
8. Upload your HTML file into the paper/ folder.
9. Update index.html so your paper appears on the homepage.
10. Open a Pull Request.

Congratulations, you are now part of the PaperMap community.

## Pull Request Checklist

1. File added inside paper/.
2. Homepage card added in index.html.
3. Links tested locally.
4. Desktop and mobile layout checked.
5. Metadata updated (title, description, social tags).

## Attribution

All explainers are educational derivatives of original research papers.
Credit always belongs to the original authors.

## License

This project is licensed under the [MIT License](LICENSE).
