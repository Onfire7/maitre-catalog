# Conversion of joplin

From `joplin`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into big-bear-joplin's POSTGRES_PASSWORD and big-bear-joplin-db's POSTGRES_PASSWORD is the setting POSTGRES_PASSWORD, made up at install
- big-bear-joplin: container_name "big-bear-joplin" is dropped; Maître names the container, and other containers reach it as "big-bear-joplin"
- big-bear-joplin-db: container_name "big-bear-joplin-db" is dropped; Maître names the container, and other containers reach it as "big-bear-joplin-db"
- big-bear-joplin-db: CasaOS's /DATA/AppData/joplin/postgresql/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/laurent22/joplin, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app and db, not after Big Bear's containers; the app reaches the database at db.
- APP_BASE_URL is the Service's address on the home network, http://<name>.local, not localhost.
- Health is its own /api/ping.
