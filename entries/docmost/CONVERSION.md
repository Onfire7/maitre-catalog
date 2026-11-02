# Conversion of Docmost

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-docmost: APP_SECRET is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-docmost-db: POSTGRES_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-docmost: container_name "big-bear-docmost" is dropped; Maître names the container, and other containers reach it as "big-bear-docmost"
- big-bear-docmost: CasaOS's /DATA/AppData/docmost/data/storage is the Service volume "storage", kept in a Storage Space
- big-bear-docmost-db: container_name "big-bear-docmost-db" is dropped; Maître names the container, and other containers reach it as "big-bear-docmost-db"
- big-bear-docmost-db: CasaOS's /DATA/AppData/docmost/data/pgdata is the Service volume "pgdata", kept in a Storage Space
- big-bear-docmost-redis: container_name "big-bear-docmost-redis" is dropped; Maître names the container, and other containers reach it as "big-bear-docmost-redis"
- big-bear-docmost-redis: CasaOS's /DATA/AppData/docmost/data/redis is the Service volume "redis", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/docmost/docmost, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app, db and redis, not after Big Bear's containers; the app reaches them at db and redis.
- APP_SECRET and the database password, written into the file, are settings made up at install.
- APP_URL is the Service's address on the home network, http://<name>.local, instead of localhost; Docmost builds the links in its emails from it.
- Health is /api/health.
- Its own volumes mount with Podman's U option: the image runs as a user other than root, and the Node makes a Service's folders as root, so without it the app could not write them (seen on a Node with Vikunja, 2026-11-02).
