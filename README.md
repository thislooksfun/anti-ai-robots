# Anti-AI Robots.txt Action

This is a simple action that will automatically keep your `robots.txt` file up-to-date with [ai-robots-txt/ai.robots.txt](https://github.com/ai-robots-txt/ai.robots.txt). It works via pull requests so you can review the changes worry-free before merging.

Usage:

```yaml
name: Update robots.txt

on:
  schedule:
    # Run at midnight (utc)
    - cron: "0 0 * * *"

permissions:
  # Create and push new branch
  contents: write
  # Create PR
  pull-requests: write

jobs:
  robots:
    runs-on: ubuntu-latest
    steps:
      - name: Update robots.txt
        uses: thislooksfun/anti-ai-robots@v1
        with:
          # The path to the robots.txt file. Useful if your static files are not
          # hosted at the root of the repository, or if you want to use a
          # different filename.
          path: robots.txt

          # The name of the branch to update. Useful if you have your website
          # hosted on a separate branch, i.e. github pages
          branch: ""

          # The commit message to use when creating the branch.
          commit-message: "chore: update robots.txt"

          # The name of the branch the PR will be made from.
          pr-branch: update-robots-txt

          # The title of the PR.
          pr-title: Update robots.txt
```
