# Conversion of NocoDB

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-nocodb: NC_AUTH_JWT_SECRET is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-nocodb-db: POSTGRES_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-nocodb: container_name "big-bear-nocodb" is dropped; Maître names the container, and other containers reach it as "big-bear-nocodb"
- big-bear-nocodb: CasaOS's /DATA/AppData/nocodb/data is the Service volume "data", kept in a Storage Space
- big-bear-nocodb-db: container_name "big-bear-nocodb-db" is dropped; Maître names the container, and other containers reach it as "big-bear-nocodb-db"
- big-bear-nocodb-db: CasaOS's /DATA/AppData/nocodb/pgdata is the Service volume "pgdata", kept in a Storage Space
- big-bear-nocodb-redis: container_name "big-bear-nocodb-redis" is dropped; Maître names the container, and other containers reach it as "big-bear-nocodb-redis"
- big-bear-nocodb-redis: CasaOS's /DATA/AppData/nocodb/redis is the Service volume "redis", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/nocodb/nocodb, NocoDB's own repository.
- The components are named app, db and redis, not after Big Bear's containers; the app reaches them at db and redis, starts after both, and waits for redis to answer.
- The session secret, the database password (nocodb in the file) and the cache password (casaos) are each a setting made up at install.
- NC_PUBLIC_URL is the Service's address on the home network, http://<name>.local, for the links NocoDB sends.
- Health is /api/v1/health.
