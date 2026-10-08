name: Setup Arctic files
on: workflow_dispatch
permissions:
  contents: write
jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: node setup.js
      - run: |
          rm setup.js
          git config user.name "github-actions"
          git config user.email "actions@github.com"
          git add -A
          git commit -m "Add Arctic project files"
          git push
