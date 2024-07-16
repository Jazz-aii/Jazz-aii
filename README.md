![Imagen](banner.png)

[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white)](https://www.instagram.com/wyx_jazz?igsh=MXBhMGQycm0yNjIxMg%3D%3D&utm_source=qr)
[![Discord](https://img.shields.io/badge/Discord-%235865F2.svg?style=for-the-badge&logo=discord&logoColor=white)](https://discordapp.com/users/1106395698611638332)

Hi👋 I'm Jazmin. I'm 16 years old. I'd like to study something with technology✨. I love to explore new things. I'm passionate learner about techonlogy, AI, programming💡. On the other hand, I enjoy to listen to music, draw, playing instruments, do activities that help me grow as a person💻🤍.

[![GitHub Streak](https://github-readme-streak-stats.herokuapp.com?user=Jazz-aii&theme=modern-lilac2&type=png)](https://git.io/streak-stats)

![Views](https://komarev.com/ghpvc/?username=Jazz-aii&abbreviated=true)


name: generate animation

on:
  # run automatically every 12 hours
  schedule:
    - cron: "0 */12 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - main
    
  

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: Generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v2
        with:
          github_user_name: Jazz-aii
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: Push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v2.6.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
