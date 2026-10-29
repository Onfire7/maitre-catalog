# Conversion of Paperless-ngx

From `paperless-ngx`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-paperless-ngx: PAPERLESS_ADMIN_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-paperless-ngx: PAPERLESS_CSRF_TRUSTED_ORIGINS=http://[YOUR_IP]:8000 holds a placeholder to fill in
- big-bear-paperless-ngx: PAPERLESS_URL=http://[YOUR_IP]:8000 holds a placeholder to fill in

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into big-bear-paperless-ngx's PAPERLESS_DBPASS and big-bear-paperless-ngx-db's POSTGRES_PASSWORD is the setting PAPERLESS_DBPASS, made up at install
- big-bear-paperless-ngx: container_name "big-bear-paperless-ngx" is dropped; Maître names the container, and other containers reach it as "big-bear-paperless-ngx"
- big-bear-paperless-ngx: CasaOS's /DATA/AppData/paperless-ngx/paperless/data is the Service volume "data", kept in a Storage Space
- big-bear-paperless-ngx: CasaOS's /DATA/AppData/paperless-ngx/paperless/media is the Service volume "media", kept in a Storage Space
- big-bear-paperless-ngx: CasaOS's /DATA/AppData/paperless-ngx/paperless/export is the Service volume "export", kept in a Storage Space
- big-bear-paperless-ngx: CasaOS's /DATA/AppData/paperless-ngx/paperless/consume is the Service volume "consume", kept in a Storage Space
- big-bear-paperless-ngx: CasaOS's /DATA/AppData/paperless-ngx/paperless/tmp is the Service volume "tmp", kept in a Storage Space
- big-bear-paperless-ngx-broker: container_name "big-bear-paperless-ngx-broker" is dropped; Maître names the container, and other containers reach it as "big-bear-paperless-ngx-broker"
- big-bear-paperless-ngx-broker: CasaOS's /DATA/AppData/paperless-ngx/redis is the Service volume "redis", kept in a Storage Space
- big-bear-paperless-ngx-db: container_name "big-bear-paperless-ngx-db" is dropped; Maître names the container, and other containers reach it as "big-bear-paperless-ngx-db"
- big-bear-paperless-ngx-db: CasaOS's /DATA/AppData/paperless-ngx/postgres is the Service volume "postgres", kept in a Storage Space
- big-bear-paperless-ngx-gotenberg: container_name "big-bear-paperless-ngx-gotenberg" is dropped; Maître names the container, and other containers reach it as "big-bear-paperless-ngx-gotenberg"
- big-bear-paperless-ngx-tika: container_name "big-bear-paperless-ngx-tika" is dropped; Maître names the container, and other containers reach it as "big-bear-paperless-ngx-tika"
- big-bear-paperless-ngx-tika: CasaOS's /DATA/AppData/paperless-ngx/tika/tmp is the Service volume "tmp_2", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PAPERLESS_SECRET_KEY is made up at install

## Edited by hand

After the conversion, for the Catalog:

- The containers take the names of Paperless-ngx's own Compose file (webserver, broker, db, gotenberg, tika) instead of big-bear-paperless-ngx-*, and every reference to them follows.
- The administrator's name (bigbear) and password, fixed in the file, are the settings PAPERLESS_ADMIN_USER (admin) and PAPERLESS_ADMIN_PASSWORD, made up at install; the database user is paperless.
- PAPERLESS_URL and PAPERLESS_CSRF_TRUSTED_ORIGINS, left as [YOUR_IP] placeholders, are removed: Caddy keeps the address the browser used, which is what Paperless checks.
- The /tmp folders of the web server and Tika are no longer kept as Service volumes.
- The time zone is the TZ setting, given to Paperless as PAPERLESS_TIME_ZONE.
