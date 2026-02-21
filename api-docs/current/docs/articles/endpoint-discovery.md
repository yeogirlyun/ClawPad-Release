# Endpoint Discovery and Dashboard

ClawPad exposes multiple discovery surfaces:

- `/docs` OpenAPI Swagger UI
- `/redoc` OpenAPI ReDoc
- `/developer/dashboard` searchable developer dashboard
- `/api/developer/dashboard` machine-readable catalog
- `/api/developer/docs` searchable long-form documentation index

## Why multiple discovery surfaces?

- OpenAPI is ideal for request execution and schema-first tooling.
- Dashboard is ideal for product-level API navigation and lookup.
- JSON discovery endpoints are ideal for automation and custom docs tooling.

## Dashboard search model

Search matches across:

- endpoint path
- endpoint summary/description
- endpoint tags/category
- developer doc title/summary/keywords/content
