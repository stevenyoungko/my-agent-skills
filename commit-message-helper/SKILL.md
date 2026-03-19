---
name: commit-message-helper
description: Helps write Git commit messages following the Conventional Commits specification. Use this skill when the user asks to commit changes, write commit messages, or mentions git commits.
---

# Commit Message Helper

When this skill is invoked, write the commit message following the rules below and immediately execute the git commit.

When writing commit messages, follow these rules:

## Format

<type>(<scope>): <ticket-number>-<subject>

## Types

- feat: A new feature
- fix: A bug fix
- docs: Documentation only changes
- style: Changes that do not affect the meaning of the code
- refactor: A code change that neither fixes a bug nor adds a feature
- perf: A code change that improves performance
- test: Adding missing tests or correcting existing tests
- chore: Changes to the build process or auxiliary tools

## Guidelines

1. Subject line should be no longer than 50 characters
2. Use imperative mood ("add feature" not "added feature")
3. Do not end the subject line with a period
4. Separate subject from body with a blank line
5. Use the body to explain what and why, not how
6. Always include the ticket number (e.g. SL-12345) after the colon, before the subject. Infer it from the branch name if not provided.

## Examples

Good:
feat(auth): SL-50436-use POST for OmniAuth login requests

Bad:
updated stuff
feat(auth): add OAuth2 login support (missing ticket number)
