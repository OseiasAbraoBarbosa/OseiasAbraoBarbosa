### Olá eu sou o Oséias Abrão Barbosa, sou um Programador Front End, atualmente estou estudando e criando projetos!
---
<br>

### Linguagens e ferramentas em desenvolvimento:

<div style="display: inline_block"><br>
<img align="center" alt="Oseias-HTML" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg">
<img align="center" alt="Oseias-CSS" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg">
<img align="center" alt="Oseias-JavaScript" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg">
<img align="center" alt="Oseias-Git" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg">
<img align="center" alt="Oseias-Github" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg">
<img align="center" alt="Oseias-Figma" height="30" width="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg">
</div>

### Conecte-se comigo:

<div>
  <p align="left"><a href="mailto:oseiasabrao2011@live.com">✉ oseiasabrao2011@live.com</a></p>
  
  <a href="https://www.linkedin.com/in/oseias-abrao-barbosa" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a>
</div>
<br>

[![Oseias stats](https://github-readme-stats.vercel.app/api?username=OseiasAbraoBarbosa)](https://github.com/anuraghazra/github-readme-stats)

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=OseiasAbraoBarbosa)](https://github.com/anuraghazra/github-readme-stats)

# Nome da Actions:  
name: Snake Game

# Controlador do tempo que sera feito a atualização dos arquivos.
on:
  schedule:
      # Será atualizado a cada 5 horas.
    - cron: "0 */5 * * *"

# Permite executar na na lista de Actions (utilizado para testes de build).
  workflow_dispatch:

# Regras
jobs:
  build:
    runs-on: ubuntu-latest
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Repositorio que será utilizado para gerar os arquivos.
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: OseiasAbraoBarbosa #Seu usuario
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

      - run: git status

      # Para as atualizações.
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

