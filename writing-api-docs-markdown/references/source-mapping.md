# Source Mapping

## Goal

Map code to documentation without relying on guesswork.

## Where to Extract Facts

### Method and Path

Look in:

- Spring: controller annotations such as `@GetMapping`, `@PostMapping`, `@RequestMapping`
- NestJS: `@Get`, `@Post`, `@Controller`
- Express/Koa/Fastify: router definitions
- FastAPI: decorator path operations
- Django/Flask: route declarations

Document:

- HTTP method
- Full path
- Path params

### Request Parameters

Look in:

- controller/handler method signature
- DTO/request object
- validation annotations or schema
- query parser / decorator definitions

Document:

- field names
- types
- required vs optional
- defaults that are actually applied

### Response Shape

Look in:

- controller return type
- wrapper helpers
- serializer/view object/DTO
- tests if they clearly assert shape

Document:

- wrapper keys such as `code`, `msg`, `data`, `rows`, `total`
- business payload fields

### Behavior Notes

Look in:

- service/use-case layer
- repository/mapper SQL
- middleware/guards/interceptors
- tests for edge-case behavior

Document:

- auth or permission checks
- tenant scoping
- ownership restrictions
- sort order
- logical delete vs physical delete
- cascade delete/update side effects
- validation errors that affect caller expectations

## Framework-Neutral Questions

Before writing an endpoint, answer these:

1. What is the exact method and path?
2. What inputs can the caller send?
3. Which fields are required?
4. What defaults are applied if the caller omits a field?
5. What response wrapper does the API really return?
6. What business data fields appear in the payload?
7. What restrictions apply to the caller's visibility or write scope?
8. What side effects happen on update or delete?
9. What is the sort order for list endpoints?

If you cannot answer one of these from code, do not invent it.

## Repo-Style Adaptation

When a repository already has API docs:

- copy the structural style
- keep the local language
- keep heading conventions
- keep example density similar

But still prefer code over existing prose when they conflict.

## Fast Checklist

- method/path verified
- request params verified
- response wrapper verified
- payload fields verified
- defaults verified
- auth or scoping verified
- sort rule verified
- delete semantics verified
