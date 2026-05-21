# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Quarto blog ("Laboratório Aberto") for documenting data science and AI studies — an open learning lab meant to help others who are also starting out. Posts are written in Python. The blog uses the **Journal** theme from Bootswatch.

## Stack

- **Quarto** 1.9.37 — site generator
- **Python** 3.14 — language for code chunks (via Jupyter)
- **VS Code** — IDE, with extensions `quarto.quarto` and `ms-python.python` installed

## Commands

Run from inside the `blog/` directory:

```bash
# Live preview (opens browser, hot reloads)
quarto preview

# Build the site
quarto render

# Create a new post
quarto create post "nome-do-post"
```

## Project Structure

```
novo_projeto/
├── blog/                     ← Quarto project root
│   ├── _quarto.yml           ← Site config (theme, title, navbar)
│   ├── index.qmd             ← Homepage (post listing)
│   ├── about.qmd             ← About page
│   ├── styles.css            ← Custom CSS
│   └── posts/
│       ├── _metadata.yml     ← Shared frontmatter for all posts
│       ├── welcome/          ← Example post
│       └── post-with-code/   ← Example post with Python code
└── 20260520/                 ← Process screenshots + notes (dated folders)
```

## Adding a Post

Each post lives in its own folder under `posts/` with an `index.qmd`:

```
posts/
└── meu-primeiro-post/
    ├── index.qmd
    └── (imagens, dados, etc.)
```

Frontmatter mínimo de um post:

```yaml
---
title: "Título do Post"
date: "2026-05-20"
categories: [python, exploração]
---
```

## Theme

The blog uses the `journal` theme (set in `_quarto.yml`). To change, replace `theme: journal` with any [Bootswatch theme name](https://quarto.org/docs/output-formats/html-themes.html).
