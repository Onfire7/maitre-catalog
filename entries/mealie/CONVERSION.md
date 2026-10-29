# Conversion of Mealie

From `mealie`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "big-bear-mealie" is dropped; Maître names the container, and other containers reach it as "app"
- app: CasaOS's /DATA/AppData/mealie/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The image is the project's own name for it, ghcr.io/mealie-recipes/mealie, as its documentation gives; docker.io/hkotel/mealie is the same image (the same digest) under its old name.
- Health is /api/app/about.
