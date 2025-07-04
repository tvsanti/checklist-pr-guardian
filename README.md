# ✅ PR Checklist Validator

This GitHub Action ensures that all required checklist items in a pull request (PR) description are completed before merging.

## 🔧 How It Works

- **Triggers on:** PR opened, edited, or synchronized.
- **Fails if:** Any checklist item is missing or incomplete.

It checks for the following items in the PR body:

```markdown
- [x] Answer 1:
- [x] Answer 2:
- [x] Answer 3:
