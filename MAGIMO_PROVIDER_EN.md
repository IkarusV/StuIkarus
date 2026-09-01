# Magimo A1111-Compatible Provider

## Configuration

1. Select the Stable Diffusion backend.
2. Set **A1111-Compatible API Base URL** to the Magimo endpoint that exposes `/sdapi/v1/*` routes.
3. Select **Bearer API key (Magimo/cloud)**.
4. Enter a per-user cloud API key in **Cloud API key**.
5. Click **Connect and Refresh** to retrieve backend metadata.

The bundled placeholder is `https://comfy.magimo.vn`. It must expose an A1111-compatible gateway, because this extension calls `/sdapi/v1/options`, `/sdapi/v1/txt2img`, and related A1111 endpoints. A ComfyUI-only endpoint is not compatible with this SD provider panel.

## Authentication

- Bearer mode sends `Authorization: Bearer <API key>`.
- Basic mode sends `Authorization: Basic <base64(username:password)>`.
- Bearer mode uses direct browser requests even when the general client setting is Tavern proxy mode. The legacy proxy request schema accepts only Basic-style credentials and must not receive cloud bearer keys.

## Requirements

- The endpoint must permit requests from the SillyTavern browser origin, or be served through a compatible gateway.
- Cloud API keys are stored in the extension settings and rendered in password fields.
- Never paste keys into prompt fields, logs, screenshots, exported configurations, or bug reports.

## Resolution Rules

Stable Diffusion dimensions must be integers from 64 through 2048 and divisible by 8. The SDXL preset selector supplies supported SDXL resolutions, while direct overrides are validated before dispatch.
