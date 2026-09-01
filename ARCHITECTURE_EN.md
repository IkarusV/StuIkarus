# Architecture

`st-chatu8` is a SillyTavern extension that adds image generation, prompt management, character data, knowledge-base tools, vocabulary tools, themes, diagnostics, and an assistant interface.

## Main Components

- `index.js`: Extension startup, settings persistence, event handlers, backend requests, generation queues, and dynamic UI behavior.
- `settings.html`: Main settings shell and assistant-related panels.
- `html/settings/*.html`: Static settings panels loaded into the main UI.
- `html/summary-manager.html`: Standalone summary-manager markup, mirrored in `settings.html` where required.

## Image Backends

- Stable Diffusion WebUI / A1111: Uses `/sdapi/v1/*` endpoints for metadata, options, and `txt2img` generation.
- ComfyUI: Uses ComfyUI API and workflow JSON stored in settings.
- NovelAI: Uses NovelAI image-generation APIs and optional proxy paths.
- Banana: Uses configured Gemini-, Grok-, or OpenAI-compatible image endpoints.

## Stable Diffusion Request Modes

- Browser mode: The extension calls the configured A1111-compatible endpoint directly. This requires that the endpoint permits the SillyTavern browser origin.
- Tavern proxy mode: Legacy Basic authentication calls use `/api/sd/*` routes on the SillyTavern server.
- Bearer mode: Cloud requests bypass the legacy proxy and make direct authenticated A1111-compatible requests. This prevents cloud API keys from being serialized in proxy request bodies that only support Basic credentials.

## Settings

Settings are held under the extension namespace in SillyTavern extension settings. UI elements use IDs as setting keys. Persisted option values, template variables, prompt payloads, workflow JSON, and parser-facing strings are retained unchanged by the English localization.
