name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"

  workflow_dispatch:

jobs:
  generate:
    runs-on: ubuntu-latest

  permissions:
      contents: write

  steps:
      - name: Generate GitHub Contribution Snake
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: Yash-Kumar-Halder
          outputs: |
            dist/github-snake.svg?color_dots=#000000,#111111,#333333,#777777,#00ffff&color_snake=#ffffff

  - name: Push Snake to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
