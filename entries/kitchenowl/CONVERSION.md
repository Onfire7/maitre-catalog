# Conversion of KitchenOwl

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- app: JWT_SECRET_KEY is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "big-bear-kitchenowl" is dropped; Maître names the container, and other containers reach it as "app"
- app: CasaOS's /DATA/AppData/kitchenowl/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/TomBursch/kitchenowl, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- JWT_SECRET_KEY is made up at install; the file wrote it in.
- FRONT_URL is the Service's address on the home network, http://<name>.local, for the links it sends.
- Health is /, the page itself; its own health route carries a fixed token in its path.
