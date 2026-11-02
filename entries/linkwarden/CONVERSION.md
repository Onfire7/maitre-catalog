# Conversion of Linkwarden

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into linkwarden's MEILI_MASTER_KEY and linkwarden-meilisearch's MEILI_MASTER_KEY is the setting MEILI_MASTER_KEY, made up at install
- The password written into linkwarden's NEXTAUTH_SECRET and linkwarden-postgres's POSTGRES_PASSWORD is the setting NEXTAUTH_SECRET, made up at install
- linkwarden: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- linkwarden: container_name "linkwarden" is dropped; Maître names the container, and other containers reach it as "linkwarden"
- linkwarden: CasaOS's /DATA/AppData/linkwarden/data is the Service volume "data", kept in a Storage Space
- linkwarden-meilisearch: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- linkwarden-meilisearch: container_name "linkwarden-meilisearch" is dropped; Maître names the container, and other containers reach it as "linkwarden-meilisearch"
- linkwarden-meilisearch: CasaOS's /DATA/AppData/linkwarden/meili_data is the Service volume "meili_data", kept in a Storage Space
- linkwarden-postgres: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- linkwarden-postgres: container_name "linkwarden-postgres" is dropped; Maître names the container, and other containers reach it as "linkwarden-postgres"
- linkwarden-postgres: CasaOS's /DATA/AppData/linkwarden/pgdata is the Service volume "pgdata", kept in a Storage Space
- linkwarden waits for linkwarden-postgres's health check through Notify=healthy, instead of compose2quadlet's polling loop, which would run on the Node
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/linkwarden/linkwarden, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app, db and search, not after CasaOS's containers; the app reaches them at db and search.
- The file's one password abc123 served as the session secret and the database password, and the search key was written in; each is its own setting, made up at install.
- NEXTAUTH_URL is the Service's address on the home network, http://<name>.local/api/v1/auth, instead of localhost; signing in with a password works from any address, a login through an outside provider would need this to be the address used.
- Health is /api/v1/logins, which answers without signing in.
