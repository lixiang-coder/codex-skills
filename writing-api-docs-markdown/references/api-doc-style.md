# API Doc Style

## Goal

Produce Markdown API docs that are easy for frontend engineers, testers, and future maintainers to scan. Use the repository's existing format when one exists; otherwise use the generic structure below.

## Default File Shape

```md
# Module API Documentation

## 1. List ...
...

## 2. Get ...
...
```

- Use one section per endpoint.
- If the repository numbers sections, keep numbering.
- If the repository does not number sections, standard endpoint headings are fine.

## Per-Endpoint Structure

```md
## 1. List Orders

Path: GET /orders

Description: List orders visible to the current user.

Request Parameters:

| Name | Type | Required | Description |
| ---- | ---- | -------- | ----------- |
| status | String | No | Filter by status |

Response Fields:

| Field | Type | Description |
| ----- | ---- | ----------- |
| id | Long | Order ID |

Request Example:

```text
GET /orders?status=paid
```

Response Example:

```json
{
  "code": 200,
  "message": "success",
  "data": []
}
```

Notes:

- Only returns the current tenant's data
- Sorted by createdAt descending
```

## Localization Rule

- Match the repository's existing language.
- If the repo already uses Chinese docs, keep Chinese headings and notes.
- If the repo already uses English docs, keep English headings and notes.

## Request Parameter Table

- Include path params, query params, and body fields when they matter to callers.
- Use columns that match repo convention when possible.
- If no repo convention exists, use:
  - `Name`
  - `Type`
  - `Required`
  - `Description`

## Response Field Table

- Include when the endpoint returns business data worth documenting.
- Skip if the endpoint only returns a generic success/failure envelope.
- If a wrapper exists, document both:
  - wrapper fields if useful
  - business fields inside the data payload

## Examples

- Use realistic values.
- Reuse the same field names as code.
- Keep request and response examples aligned with each other.
- Do not mix snake_case and camelCase unless the API actually does.

## Notes / 说明

- Keep this section short and high-signal.
- Good note topics:
  - tenant scoping
  - ownership rules
  - auth/permission requirements
  - default values
  - sort order
  - logical vs physical delete
  - cascade effects
  - special validation behavior

## Common Mistakes

- Documenting framework defaults instead of actual code behavior
- Guessing pagination
- Guessing delete semantics
- Guessing auth requirements
- Using model field names instead of API field names
- Copying an old wrapper shape into a new endpoint
