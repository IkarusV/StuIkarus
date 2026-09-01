# Security Audit

## Reviewed Scope

- Stable Diffusion URL, Basic authentication, Bearer cloud authentication, generation, model switching, metadata refresh, and proxy behavior.
- Settings persistence and password input controls.

## Remediated Findings

| Finding | Resolution |
| --- | --- |
| Bearer keys were not supported by the legacy Tavern SD proxy request schema. | Bearer mode now bypasses the Basic-only proxy and sends direct authenticated A1111-compatible requests. |
| Existing Magimo endpoint settings without an auth type defaulted to Basic. | Migration chooses Bearer for `magimo.vn` endpoints and Basic for other endpoints. |
| SD dimensions accepted invalid or excessive values. | Generation validates dimensions as 64-2048 integer multiples of 8; UI inputs provide matching bounds and step. |
| SD generation payloads were logged to the browser console. | The direct SD payload console log is removed. |
| SD auth controls lacked an explicit settings mapping. | `sd_auth_type` and `sd_api_key` are included in the SD settings mapping. |

## Remaining Operational Risks

- Direct Bearer requests require CORS support by the configured cloud gateway.
- Other provider modules may still log prompts or provider responses. This audit targeted the Magimo/A1111 SD integration; broad provider log-redaction is a separate review.
- API credentials reside in browser-accessible extension settings by design. Treat the SillyTavern profile and exported settings as sensitive.

## Logging Guidance

Do not log Authorization headers, API keys, passwords, bearer tokens, raw request bodies, raw error bodies, or base64 image payloads. Prefer endpoint category, HTTP status, and a bounded status message.
