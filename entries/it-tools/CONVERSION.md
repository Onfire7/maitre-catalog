# Conversion of IT Tools

From `it-tools`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "big-bear-it-tools" is dropped; Maître names the container, and other containers reach it as "app"
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The version is the tag's date, 2023.11.2, without its commit.
