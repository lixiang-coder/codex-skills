---
name: writing-api-docs-markdown
description: Use when writing or updating Markdown API documentation for backend endpoints after changing controllers, routes, services, DTOs, or response wrappers, especially when code should be treated as the source of truth and the docs need parameter tables, response field tables, request or response examples, and behavior notes.
---

# Writing API Docs Markdown

## Overview

Write clean, code-aligned Markdown API docs for backend endpoints. Adapt the output to the target repository's existing doc style and language, but always derive behavior from code rather than guessing from conventions.

## Workflow

1. Read the route/controller/handler first to confirm HTTP method and full path.
2. Read the service/use-case layer to confirm validation, default values, access rules, sort rules, and deletion semantics.
3. Read DTOs, domain models, serializers, or mapper XML only as needed to confirm field names and response shapes.
4. Read one or two existing docs in the repo to match heading style, language, and example density.
5. Use [references/api-doc-style.md](references/api-doc-style.md) for the document structure.
6. Use [references/source-mapping.md](references/source-mapping.md) when mapping code into request and response documentation.

## Non-Negotiables

- Treat code as the source of truth.
- Match field names exactly as returned by the API.
- Match the actual response wrapper instead of assuming one.
- Document only the behavior that the code clearly implements.
- Keep examples realistic and internally consistent.
- Mention logical delete, pagination, authorization, tenant scoping, ownership limits, and cascade effects when they are implemented.

## Do Not Guess

- Do not invent query params, body fields, enum values, or default values.
- Do not invent permissions, auth requirements, or tenant rules if they are not visible in code or clearly implied by middleware/decorators.
- Do not assume DELETE means physical delete.
- Do not assume list endpoints are paginated.
- Do not assume success wrappers such as `data`, `rows`, `result`, or `items`; confirm the real shape.

## Output Rules

- Prefer Markdown tables for request and response fields.
- Use fenced `json` blocks for JSON examples.
- Use fenced `text` blocks for raw URL examples.
- Organize endpoints in a predictable order:
  - list
  - detail
  - create
  - update
  - delete
  - extra operations
- If the repo already uses numbered sections, preserve that convention.
- If the repo already uses Chinese or English, preserve that language.

## Adaptation Rule

- Follow the repo's local documentation style first.
- If the repo has no clear style, use the generic structure in [references/api-doc-style.md](references/api-doc-style.md).
- If the repo has a strong house style, adapt headings and wording while keeping the same verification discipline.

## When to Use the References

- Always read [references/api-doc-style.md](references/api-doc-style.md) before drafting a new doc file.
- Read [references/source-mapping.md](references/source-mapping.md) whenever request fields, response wrappers, auth behavior, sort rules, or delete semantics are not obvious from the route definition alone.
