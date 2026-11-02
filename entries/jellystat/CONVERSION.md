# Conversion of Jellystat

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-jellystat: JWT_SECRET is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into big-bear-jellystat's POSTGRES_PASSWORD and big-bear-jellystat-db's POSTGRES_PASSWORD is the setting POSTGRES_PASSWORD, made up at install
- big-bear-jellystat: container_name "big-bear-jellystat" is dropped; Maître names the container, and other containers reach it as "big-bear-jellystat"
- big-bear-jellystat: CasaOS's /DATA/AppData/jellystat/backup-data is the Service volume "backup_data", kept in a Storage Space
- big-bear-jellystat-db: container_name "big-bear-jellystat-db" is dropped; Maître names the container, and other containers reach it as "big-bear-jellystat-db"
- big-bear-jellystat-db: CasaOS's /DATA/AppData/jellystat/postgres-data is the Service volume "postgres_data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/CyferShepard/Jellystat, Jellystat's own repository.
- The components are named app and db, not after Big Bear's containers; the app reaches the database at db and starts after it.
- The session secret and the database password are each a setting made up at install; the file wrote them in.
