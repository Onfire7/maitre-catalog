# Conversion of Excalidraw

From `Excalidraw`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- excalidraw: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- excalidraw: container_name "excalidraw" is dropped; Maître names the container, and other containers reach it as "excalidraw"
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
