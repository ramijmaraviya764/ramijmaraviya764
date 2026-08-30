name: Generate Snake Animation

on:
  schedule:
    # Runs once a day at 00:00 UTC. Change the cron expression if you want a different frequency.
    - cron: "0 0 * * *"
  workflow_dispatch: {}   # Allows manual runs from the Actions tab
  push:
    branches:
      - main             # Regenerates whenever you push to your main branch

permissions:
  contents: write

jobs:
  generate-snake:
    runs-on: ubuntu-latest
    steps:
      - name: Generate contribution snake SVG
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: ramijmaraviya764
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push generated files to the "output" branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
