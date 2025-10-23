# 🤖 Pollinations AI Issue Bot

Turn GitHub issues into Pull Requests using AI.

**Usage:**
```yaml
on:
  issues:
    types: [opened]
jobs:
  ai:
    runs-on: ubuntu-latest
    steps:
      - uses: cloudcompile/pollinations-ai-issue-bot@v1.1.0
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          pollinations-api: https://text.pollinations.ai/openai
