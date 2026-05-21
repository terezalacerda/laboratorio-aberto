# Referência de Comandos

Guia rápido de todos os comandos usados no projeto. Salvo aqui para não precisar ficar pesquisando.

---

## Quarto

> Todos os comandos Quarto rodam de dentro da pasta `blog/`

```bash
# Ver o blog no navegador com live reload
quarto preview

# Renderizar o site sem abrir o navegador (só gera os arquivos)
quarto render

# Criar um novo post (cria a pasta e o index.qmd automaticamente)
quarto create post "nome-do-post"

# Publicar no GitHub Pages
quarto publish gh-pages --no-prompt
```

---

## Git — fluxo do dia a dia

> Rodar da raiz do projeto (`novo_projeto/`)

```bash
# Ver o que mudou
git status
git diff

# Salvar alterações
git add .
git commit -m "descrição do que mudou"
git push
```

---

## Fluxo completo: escrever e publicar um post

```bash
# 1. criar o post
cd blog
quarto create post "nome-do-post"

# 2. escrever o conteúdo em blog/posts/nome-do-post/index.qmd
#    (usar VS Code)

# 3. ver como ficou antes de publicar
quarto preview

# 4. salvar no GitHub (código-fonte)
cd ..                              # volta para novo_projeto/
git add .
git commit -m "post: nome do post"
git push

# 5. publicar o site
cd blog
quarto publish gh-pages --no-prompt
```

---

## GitHub CLI (`gh`)

```bash
# Verificar autenticação
gh auth status

# Criar repositório (usado na criação inicial)
gh repo create nome-do-repo --public --description "descrição" --source . --remote origin --push
```

---

## Git — comandos úteis extras

```bash
# Ver histórico de commits
git log --oneline

# Ver em qual branch está
git branch

# Verificar conexão com o GitHub
git remote -v
```

---

## Instalações (referência — já feitas)

Caso precise reconfigurar em outra máquina:

```powershell
# Quarto
winget install --id Posit.Quarto --accept-package-agreements --accept-source-agreements

# VS Code
winget install --id Microsoft.VisualStudioCode --accept-package-agreements --accept-source-agreements

# GitHub CLI
winget install --id GitHub.cli --accept-package-agreements --accept-source-agreements

# Extensões do VS Code (rodar após instalar o VS Code)
code --install-extension quarto.quarto
code --install-extension ms-python.python

# Jupyter (para rodar Python nos posts)
pip install jupyter

# Autenticar GitHub CLI
gh auth login
```

---

## Links úteis

- Blog publicado: https://terezalacerda.github.io/laboratorio-aberto
- Repositório: https://github.com/terezalacerda/laboratorio-aberto
- Documentação Quarto: https://quarto.org/docs/websites/website-blog.html
- Temas disponíveis: https://quarto.org/docs/output-formats/html-themes.html
