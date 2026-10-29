# Conversion of Open WebUI

From `open-webui`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-open-webui: container_name "big-bear-open-webui" is dropped; Maître names the container, and other containers reach it as "big-bear-open-webui"
- big-bear-open-webui: CasaOS's /DATA/AppData/open-webui/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/open-webui/open-webui, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The image is the newest release, v0.12.5, instead of a git build.
- OLLAMA_BASE_URL is a setting, the Ollama Service on the same Node by default; the empty OPENAI_API_KEY is dropped (set it in its admin settings).
- Health is its own /health.
