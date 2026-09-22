---
name: orbscan-docs
description: Use when writing, reviewing, or restructuring Orbscan API documentation, Mintlify MDX pages, docs.json navigation, or openapi.json endpoint definitions in this repository.
---

# Orbscan documentation

Write Orbscan documentation that is accurate, concise, and easy to scan.

## Source of truth

- Verify behavior against an authoritative API contract or the live API before documenting it.
- Do not invent response messages, status codes, limits, defaults, or field semantics.
- Keep request and response schemas in `openapi.json`.
- Put alternate response samples in named OpenAPI `examples` so Mintlify renders them with the endpoint.
- Do not repeat generated schemas or full response samples in MDX.
- Use MDX for context, workflows, caveats, and links between endpoints.

## Writing style

- Use active voice and address the reader as "you".
- Keep sentences short and give each sentence one main idea.
- Use sentence case for headings.
- Do not use em dashes or en dashes. Use a period, comma, colon, or words such as "to" instead.
- Prefer plain verbs such as "get", "list", "send", and "return".
- Avoid filler, repeated summaries, and phrases such as "simply" or "seamlessly".
- Format field names, paths, status codes, and literal values as code.
- Preserve the API's exact casing, including `status_code`, `tokenId`, and `price_change`.

## Endpoint workflow

1. Add or update the path, parameters, responses, schemas, and examples in `openapi.json`.
2. Add a focused MDX page with `openapi: "openapi.json METHOD /path"` frontmatter.
3. Add the page to `docs.json` navigation.
4. Update overview or landing pages only when the endpoint changes the documented API surface.
5. Link related pages instead of restating their content.

## Error documentation

- Use the HTTP status for the error category and the response envelope for API details.
- Show exact `message` values only when verified.
- Document successful empty results separately from `404` responses.
- Link references such as empty-result behavior directly to their heading anchor.
- Do not publish deployment-specific rate limits unless they have been verified against production configuration.

## Checks

- Parse `openapi.json` and `docs.json` as JSON.
- Run `mint validate` when the Mintlify CLI is available.
- Confirm every MDX `openapi` reference matches an operation in `openapi.json`.
- Confirm every new navigation path resolves to an MDX file.
- Check changed prose for em dashes, duplicate schema sections, and duplicate response samples.
- Never place a real API key in documentation, source files, commands intended for publication, or examples.
