# .github/workflows/snake.yml
# Gera a animacao da "cobrinha" de contribuicoes e publica na branch `output`.
name: Generate Snake Animation

on:
  schedule:
    # Roda a cada 12 horas (atualiza a cobrinha automaticamente)
    - cron: "0 */12 * * *"
  # Permite rodar manualmente pela aba Actions
  workflow_dispatch:
  # Roda sempre que houver push na branch principal
  push:
    branches:
      - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    steps:
      - name: Generate snake game from github contribution grid
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: Dev-Gabrielcarvalho07
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark&color_snake=6fffe9&color_dots=1c2541,3a506b,5bc0be,6fffe9,e0fbfc

      - name: Push snake animation to the output branch
        uses: crazy-max/ghaction-github-pages@v4.0.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
