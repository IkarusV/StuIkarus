# Test Report

## Performed

- Ran `node --check index.js` after Magimo authentication and SD validation changes.
- Verified Bearer-mode SD model, metadata, and generation branches use direct A1111-compatible requests.
- Verified legacy Tavern proxy branches remain restricted to non-Bearer authentication.
- Verified SD dimension controls specify `min="64"`, `max="2048"`, and `step="8"`.
- Verified the SDXL preset list contains only the requested resolutions.

## Not Performed

- Browser runtime testing was not run because no local SillyTavern installation/runtime was located in the workspace.
- No credit-consuming cloud generation was performed.

## Manual Runtime Checks

1. Open the extension settings and select Stable Diffusion.
2. Confirm the SD panel is fully English and preset changes update Width and Height.
3. Configure a non-sensitive test A1111 endpoint with Basic authentication and verify proxy mode.
4. Configure a permitted Magimo A1111-compatible gateway and verify Bearer mode from browser mode.
5. Confirm invalid resolutions, such as `1025x1024`, are rejected before an image request is sent.
