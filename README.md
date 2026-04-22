# codex-skills

Personal Codex skills that I sync across machines.

## Included Skills

### `writing-api-docs-markdown`

Write or update Markdown API documentation for backend endpoints.

Use it when you need docs that are:

- aligned with controller or route code
- based on real request and response fields
- clear about validation, sorting, auth, tenant scope, and delete behavior
- adapted to the repository's existing documentation style

Skill path:

```text
writing-api-docs-markdown/
```

## Repository Structure

```text
codex-skills/
  writing-api-docs-markdown/
    SKILL.md
    agents/
    references/
```

## Install On Another Computer

Clone this repository, then copy the skill folders into your local Codex skills directory.

Typical Windows path:

```text
C:\Users\<your-user>\.codex\skills\
```

Example:

```powershell
Copy-Item '.\writing-api-docs-markdown' "$HOME\.codex\skills" -Recurse -Force
```

Then restart Codex or open a new session so the skill can be discovered.

## Usage Example

```text
Use $writing-api-docs-markdown to draft or update Markdown API documentation for these backend endpoints.
```

## Notes

- This repository is intended for custom skills only.
- System skills from `.codex/skills/.system` do not need to be copied here.
