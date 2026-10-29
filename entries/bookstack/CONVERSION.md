# Conversion of bookstack

From `bookstack`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-bookstack: APP_KEY is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-bookstack-db: MYSQL_ROOT_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into big-bear-bookstack's DB_PASSWORD and big-bear-bookstack-db's MYSQL_PASSWORD is the setting DB_PASSWORD, made up at install
- big-bear-bookstack: container_name "big-bear-bookstack" is dropped; Maître names the container, and other containers reach it as "big-bear-bookstack"
- big-bear-bookstack: CasaOS's /DATA/AppData/bookstack/config is the Service volume "config", kept in a Storage Space
- big-bear-bookstack-db: container_name "big-bear-bookstack-db" is dropped; Maître names the container, and other containers reach it as "big-bear-bookstack-db"
- big-bear-bookstack-db: CasaOS's /DATA/AppData/bookstack/mysql is the Service volume "mysql", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app and db, not after Big Bear's containers; the app reaches the database at db.
- APP_KEY is made up at install as Laravel wants it (base64: and 32 random bytes), not the one written into the file.
- The database's root password is made up at install (DB_ROOT_PASSWORD).
- APP_URL is the Service's address on the home network, http://<name>.local, instead of the file's placeholder.
- Health is its own /status.
