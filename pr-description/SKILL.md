---
name: pr-description
description: Helps write PR descriptions. Use this skill when the user asks to write a PR description, or mentions pull request.
---

# PR Description Helper

When writing a PR description, follow these rules:

## Steps

1. Run `git log <base-branch>..<current-branch> --oneline` to get all commits
2. Run `git diff <base-branch>...<current-branch>` to get all changes
3. For each commit, run `git show <hash>` if you need more context
4. Write the PR description based on the changes

## Format

## Why?

<Explain the problem or the reason behind this change. Focus on the "why", not the "what".>

---

## How?

<Explain the solution in plain, simple language. Avoid jargon. Keep it short and easy to understand.>

---

## Test Plan

- [ ] <Step to verify the change works>
- [ ] <Edge case or regression to check>

## Guidelines

- **Why**: Describe the root cause or motivation. Not what was changed, but why it needed to change.
- **How**: Keep it simple and easy to understand. Assume the reader is not familiar with the implementation details. No need to paste code unless it's very short and helps clarify.
- **Test Plan**: Focus on user-facing behavior. Each item should be something a reviewer can actually verify.
- Only include sections that are relevant. If there's nothing meaningful to say in a section, omit it.
- Write in the same language the user is using.
