# Conversion of Monica

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- monica: [Service] MemoryMax= (from x-systemd) is not carried over; it would run on the Node itself

## Changed for you

Done differently from the Compose file; check they suit the app.

- monica's APP_KEY is a placeholder ("ChangeMeBy32KeyLengthOrGenerated"); it is the setting APP_KEY, made up at install
- The password written into monica's DB_PASSWORD and monica-db's MARIADB_PASSWORD is the setting DB_PASSWORD, made up at install
- monica: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- monica: container_name "monica" is dropped; Maître names the container, and other containers reach it as "monica"
- monica: CasaOS's /DATA/AppData/monica/storage is the Service volume "storage", kept in a Storage Space
- monica-db: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- monica-db: container_name "monica-db" is dropped; Maître names the container, and other containers reach it as "monica-db"
- monica-db: CasaOS's /DATA/AppData/monica/mysql is the Service volume "mysql", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/monicahq/monica, Monica's own repository.
- The components are named app and db, not after CasaOS's containers; the app reaches the database at db.
- APP_KEY is made up at install as 32 letters and digits, the length Monica asks for; the file's placeholder said to change it.
- APP_URL is the Service's address on the home network, http://<name>.local, and APP_TRUSTED_PROXIES is * since the only way to it is the Node's proxy.
- The file's memory limit is not carried over; Maître sets none.
