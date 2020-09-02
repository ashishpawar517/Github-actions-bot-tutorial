# Github-actions-bot-tutorial 


see this using Github API

```yaml
name: commit comment
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - name: Add commit comment
        run: |
          git clone https://github.com/pawarashish564/Infinite-Series-Calculator.git
          cd Infinite-Series-Calculator
          export a="hello world"
          jq -nc '{"body":env.a}' | \
          curl -sL  -X POST -d @- \
            -H "Content-Type: application/json" \
            -H "Authorization: token ${{ secrets.GITHUB_TOKEN }}" \
            "https://api.github.com/repos/$GITHUB_REPOSITORY/commits/$GITHUB_SHA/comments"

```
