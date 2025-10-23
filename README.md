# Pollinations AI Issue Bot 🤖

Automatically responds to GitHub issues and comments using **Pollinations AI**. This Marketplace-ready GitHub Action supports auto-comments, slash commands, Markdown responses, auto-labeling, and severity estimation.

---

## Features

- **Auto-comment** on every new issue
- **Slash command support**:
  - `/ai` → full AI response
  - `/summarize` → summarizes issue
  - `/classify` → predicts labels (Bug / Feature / Question)
  - `/suggest` → proposes solutions
- **Markdown-styled responses**
- **Auto-labels** issues based on AI classification
- **Severity estimation** (Low / Medium / High)
- **Configurable AI model and referrer**

---

## Inputs

| Input | Description | Default |
|-------|-------------|---------|
| `model` | AI model to use | `openai` |
| `referrer` | Referrer for Pollinations AI | `prisimai.github.io` |

## Outputs

| Output | Description |
|--------|-------------|
| `ai_response` | The AI-generated comment to post |
| `ai_label` | Label suggested by AI |

---

## Usage

### Step 1: Add Workflow

Create `.github/workflows/issue-bot.yml`:

```yaml
name: Pollinations Issue Assistant

on:
  issues:
    types: [opened, edited]
  issue_comment:
    types: [created]

jobs:
  ai-comment:
    runs-on: ubuntu-latest
    steps:
      - uses: Cloudcompile/pollinations-issue-assistant@v1
        with:
          model: openai
          referrer: prisimai.github.io
```

### Step 2: Comment Commands

You can trigger the bot manually in any issue comment:

- `/ai` → full AI response
- `/summarize` → summarize the issue
- `/classify` → classify the issue type
- `/suggest` → propose solutions

If no command is provided, the bot will **auto-comment on all new issues**.

### Step 3: Outputs & Labels

- The AI-generated comment is stored in the `ai_response` output.
- Suggested labels (`Bug`, `Feature`, `Question`) are stored in `ai_label` and applied automatically to the issue.
- Severity estimation is included in the comment for human reference.

---

## Example Comment

**Pollinations AI Response (auto):**

> This issue appears to be a bug causing the login to fail when using Safari. Suggested steps: check browser compatibility and update dependencies.

**Labels:** Bug | **Severity:** High

---

## License

MIT License
