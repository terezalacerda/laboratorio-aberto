# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

"Laboratório Aberto" — blog pessoal de estudos em ciência de dados e IA, escrito em Python, publicado no GitHub Pages. Tem caráter de laboratório aberto: documentar experimentos e aprendizados de forma acessível a quem também está começando.

- **URL pública:** https://terezalacerda.github.io/laboratorio-aberto
- **Repositório:** https://github.com/terezalacerda/laboratorio-aberto

## Stack

- **Quarto** 1.9.37 — gerador do site
- **Python** 3.14 — linguagem dos code chunks (via Jupyter)
- **VS Code** — IDE, com extensões `quarto.quarto` e `ms-python.python`
- **GitHub Pages** — hospedagem (branch `gh-pages`)

## Estrutura do projeto

```
novo_projeto/                  ← raiz do repositório git
├── CLAUDE.md
├── COMANDOS.md                ← referência rápida de comandos
├── .gitignore
├── blog/                      ← raiz do projeto Quarto
│   ├── _quarto.yml            ← configuração do site (tema, título, site-url)
│   ├── index.qmd              ← homepage (listagem de posts)
│   ├── about.qmd              ← página about
│   ├── styles.css             ← CSS customizado
│   └── posts/
│       ├── _metadata.yml      ← frontmatter compartilhado entre posts
│       └── nome-do-post/      ← cada post em sua própria pasta
│           ├── index.qmd
│           └── (imagens, dados...)
└── AAAAMMDD/                  ← pastas com screenshots e notas de processo
```

**Importante:** a raiz do git é `novo_projeto/`, mas os comandos Quarto (`quarto preview`, `quarto publish`, etc.) devem ser rodados de dentro de `blog/`.

## Adicionando um post

```bash
cd blog
quarto create post "nome-do-post"
```

Frontmatter mínimo do `index.qmd`:

```yaml
---
title: "Título do Post"
date: "2026-05-21"
categories: [python, exploração]
description: "Resumo curto que aparece na listagem."
---
```

Imagens e dados ficam na mesma pasta do `index.qmd`. Screenshots de processo vão na pasta datada na raiz (`AAAAMMDD/`), e podem ser copiados para a pasta do post se forem usados como ilustração.

## Publicação

Dois branches com papéis distintos:
- `master` — código-fonte (`.qmd`, imagens, config)
- `gh-pages` — HTML gerado pelo Quarto (nunca editar manualmente)

**Fluxo completo para publicar:**

```bash
# 1. salvar o código-fonte no master
cd novo_projeto   # raiz do git
git add .
git commit -m "post: descrição"
git push

# 2. publicar o site (rodar de dentro de blog/)
cd blog
quarto publish gh-pages --no-prompt
```

## Gotchas aprendidos neste projeto

- **PATH do Python:** os scripts do Jupyter ficam em `C:\Users\terezacris\AppData\Local\Python\pythoncore-3.14-64\Scripts`. Já foi adicionado ao PATH do usuário, mas se o Quarto reclamar de `jupyter` não encontrado, verificar isso primeiro.
- **`quarto preview` e posts novos:** o servidor de preview não detecta arquivos `.qmd` criados depois que ele foi iniciado. Ao criar um post novo, reiniciar o preview (`Ctrl+C` e `quarto preview` de novo).
- **`site-url` obrigatório:** sem ele, o feed RSS não é gerado. Já está configurado em `_quarto.yml`.
- **`gh auth login` no terminal bash do Claude Code:** o `gh` instalado via winget não aparece no bash embutido do Claude Code. Usar PowerShell ou um terminal externo para autenticar.
- **`.claude/` no gitignore:** a pasta `.claude/` contém configurações locais do Claude Code e não deve ir para o repositório.
