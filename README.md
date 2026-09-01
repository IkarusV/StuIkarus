# StuIkarus

StuIkarus is a friendly English translation and maintained compatibility fork of
[st-chatu8](https://github.com/damoshen123/st-chatu8), a text-to-image extension
for [SillyTavern](https://github.com/SillyTavern/SillyTavern).

The GitHub repository is named **StuIkarus**. The installed extension keeps the
internal name `st-chatu8` so existing settings, selectors, parser tokens, and
SillyTavern compatibility continue to work.

## What This Fork Adds

- A friendly English interface while preserving parser-facing values and
  configuration compatibility.
- Correct automatic LLM prompt requests for body-image generation.
- A built-in image-generation context fallback when the selected context preset
  is empty, so the LLM receives a valid request instead of zero messages.
- Awaited automatic generation with persistent, visible error notifications.
- Modern A1111/Forge request payloads with numeric `steps`, `cfg_scale`,
  high-resolution scale, denoising strength, and second-pass step values.
- Configurable custom authorization headers for proxied SD A1111/Forge requests,
  including services that require bearer-token authentication.
- Stable Diffusion, NovelAI, and ComfyUI generation support inherited from the
  original extension.

No API keys or credentials are included in this repository. Configure them in
SillyTavern and avoid sharing exported settings or server logs that contain
private values.

## Installation

1. Open SillyTavern's **Extensions** panel.
2. Select **Install extension**.
3. Enter:

   ```text
   https://github.com/IkarusV/StuIkarus
   ```

4. Restart SillyTavern if prompted.
5. Open the extension settings under `st-chatu8`.

## Configuration

### Automatic LLM Image Prompts

Configure the extension's **LLM -> Body Image Generation** profile with an API
URL, API key, model, and context preset. This profile is separate from other
SillyTavern extension/provider profiles.

If the selected image-generation context contains no usable messages, StuIkarus
uses a built-in fallback request. Custom non-empty context presets remain
unchanged.

Automatic image generation runs after an eligible character response when the
feature is enabled. Very short replies are skipped by design.

### SD A1111 / Forge

Select the Stable Diffusion backend and configure the API endpoint and generation
parameters. Requests use modern JSON value types expected by current A1111/Forge
schemas. Proxy requests can include the configured custom authorization header
for authenticated SD services.

### Other Backends

NovelAI and ComfyUI retain their existing configuration panels, prompt presets,
workflow support, and generation options.

## Compatibility Notes

Some internal Chinese values remain intentionally unchanged. They are stored IDs,
replacement modes, templates, workflow fields, prompts, or parser tokens rather
than untranslated interface text. Changing them would break existing settings or
generation behavior.

## Credits

- Original extension: [damoshen123/st-chatu8](https://github.com/damoshen123/st-chatu8)
- English compatibility fork and request updates: [IkarusV](https://github.com/IkarusV)

## License

This fork retains the original project's [Aladdin Free Public License](LICENSE).
Review its terms before redistributing or using this project commercially.
