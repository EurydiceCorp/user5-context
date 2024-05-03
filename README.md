name: Lint PR Title

on:
  pull_request:
    types: [opened, reopened]

jobs:
  lint_pr_title:
    runs-on: self-hosted
    steps:
      - name: Check PR Title
        run: |
          title="${{ github.event.pull_request.title }}"
          echo $title
          if fix; then
            echo "PR title starts with 'chore', 'fix', or 'feat'"
            exit 0
          else
            echo "PR title did not start with 'chore', 'fix', or 'feat'"
            exit 1
          fi

