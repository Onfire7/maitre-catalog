# Conversion of Vikunja v2

From `vikunja-v2`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- vikunja-v2-db: MYSQL_ROOT_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value
- vikunja-v2: VIKUNJA_SERVICE_PUBLICURL=http://<your public frontend url with slash>/ holds a placeholder to fill in

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into vikunja-v2's VIKUNJA_DATABASE_PASSWORD and vikunja-v2-db's MYSQL_PASSWORD is the setting VIKUNJA_DATABASE_PASSWORD, made up at install
- vikunja-v2: container_name "big-bear-vikunja-v2" is dropped; Maître names the container, and other containers reach it as "vikunja-v2"
- vikunja-v2: CasaOS's /DATA/AppData/vikunja/files is the Service volume "files", kept in a Storage Space
- vikunja-v2-db: container_name "vikunja-v2-db" is dropped; Maître names the container, and other containers reach it as "vikunja-v2-db"
- vikunja-v2-db: CasaOS's /DATA/AppData/vikunja/mysql is the Service volume "mysql", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/go-vikunja/vikunja, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app and db, not after Big Bear's containers; the app reaches the database at db.
- The database's root password is made up at install (DB_ROOT_PASSWORD).
- VIKUNJA_SERVICE_PUBLICURL is the Service's address on the home network, http://<name>.local/, instead of the file's placeholder.
- Health is /api/v1/info.
