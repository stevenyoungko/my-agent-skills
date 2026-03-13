---
name: create-branch
description: Creates a new git branch based on a Shopline ticket title. Use this skill when the user provides a ticket title or ticket number and wants to create a branch. Branch format is <prefix>/SL-XXXXX-kebab-case-title.
disable-model-invocation: true
---

# Create Branch

The user will provide a Shopline ticket title (which includes a ticket number like SL-XXXXX).

## Branch Prefix

Supported prefixes: `feature`, `hotfix`, `integration`

- Default prefix is `feature` unless the user specifies otherwise
- If the user mentions "hotfix" or "integration", use the corresponding prefix

## Base Branch

- `feature` and `integration` branches must be created from `dev`
- `hotfix` branches must be created from `master`

## Steps

1. Determine the prefix (`feature` by default, or as specified by the user)
2. Parse the ticket number (e.g., `SL-50474`) from the input
3. Convert the remaining title (excluding the ticket number) to a concise kebab-case slug:
   - If the title is in Chinese or non-ASCII, translate it to English first
   - Summarize the core meaning — keep it short (3–5 words max)
   - Lowercase all letters
   - Replace spaces and special characters with hyphens
   - Remove any characters that are not alphanumeric or hyphens
   - Collapse multiple consecutive hyphens into one
   - Trim leading/trailing hyphens
   - The final slug (after the ticket number) should be no longer than 40 characters
4. Construct the branch name: `<prefix>/SL-XXXXX-<kebab-case-title>`
5. Determine the base branch:
   - If prefix is `feature` or `integration`: run `git fetch origin dev && git checkout -b <branch-name> origin/dev`
   - If prefix is `hotfix`: run `git fetch origin master && git checkout -b <branch-name> origin/master`
6. Confirm the branch was created successfully

## Examples

Input: `SL-50436 Modify Facebook Google Login Method`
Output branch: `feature/SL-50436-modify-facebook-google-login-method`

Input (long title): `SL-49964 Fix - 廣播發送時間非整點導致無法成功發送`
Output branch: `feature/SL-49964-fix-broadcast-schedule-send-failure`

Input (with hotfix): `SL-50436 Modify Facebook Google Login Method` (prefix: hotfix)
Output branch: `hotfix/SL-50436-modify-facebook-google-login-method`

## Notes

- The ticket number must remain in its original format (e.g., `SL-50436`)
- Strip the ticket number from the title portion to avoid duplication
- If the user provides only a title without a ticket number, ask them to provide the full ticket title including the SL number
