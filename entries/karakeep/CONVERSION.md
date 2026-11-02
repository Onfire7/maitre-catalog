# Conversion of Karakeep

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into karakeep's MEILI_MASTER_KEY and karakeep's NEXTAUTH_SECRET and karakeep-meilisearch's MEILI_MASTER_KEY is the setting MEILI_MASTER_KEY, made up at install
- karakeep: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- karakeep: container_name "karakeep" is dropped; Maître names the container, and other containers reach it as "karakeep"
- karakeep: CasaOS's /DATA/AppData/karakeep/data is the Service volume "data", kept in a Storage Space
- karakeep-chrome: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- karakeep-chrome: container_name "karakeep-chrome" is dropped; Maître names the container, and other containers reach it as "karakeep-chrome"
- karakeep-meilisearch: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- karakeep-meilisearch: container_name "karakeep-meilisearch" is dropped; Maître names the container, and other containers reach it as "karakeep-meilisearch"
- karakeep-meilisearch: CasaOS's /DATA/AppData/karakeep/meilisearch is the Service volume "meilisearch", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/karakeep-app/karakeep, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app, chrome and search, not after CasaOS's containers; the app reaches them at chrome and search, and starts after both.
- The file's one placeholder served as the session secret and the search key; each is its own setting, made up at install. The OpenAI key is a setting too, empty by default.
- NEXTAUTH_URL is the Service's address on the home network, http://<name>.local, instead of localhost on CasaOS's port.
- The chrome image is tagged release, which the project moves; it is pinned by digest and updated with the entry.
- Health is /api/health.
