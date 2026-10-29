# Conversion of Speedtest Tracker

From `speedtest-tracker`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into big-bear-speedtest-tracker's DB_PASSWORD and big-bear-speedtest-tracker-db's MARIADB_PASSWORD is the setting DB_PASSWORD, made up at install
- big-bear-speedtest-tracker: container_name "big-bear-speedtest-tracker" is dropped; Maître names the container, and other containers reach it as "big-bear-speedtest-tracker"
- big-bear-speedtest-tracker: TZ=America/Chicago is replaced by the TZ setting, the Node's time zone unless changed
- big-bear-speedtest-tracker: the host's /etc/localtime is replaced by the TZ setting, the Node's time zone unless changed
- big-bear-speedtest-tracker: CasaOS's /DATA/AppData/speedtest-tracker/config is the Service volume "config", kept in a Storage Space
- big-bear-speedtest-tracker: CasaOS's /DATA/AppData/speedtest-tracker/web is the Service volume "web", kept in a Storage Space
- big-bear-speedtest-tracker-db: container_name "big-bear-speedtest-tracker-db" is dropped; Maître names the container, and other containers reach it as "big-bear-speedtest-tracker-db"
- big-bear-speedtest-tracker-db: CasaOS's /DATA/AppData/speedtest-tracker/mysql is the Service volume "mysql", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- One container, with SQLite, instead of the app and MariaDB: SQLite is the database Speedtest Tracker's documentation installs first, and it keeps nothing that needs a server.
- APP_KEY, which the app requires, is a setting made up at install; the file has none.
- Its HTTPS port (443, published as 8443) is dropped: Maître serves the page over its own connection.
- Health is its own /api/healthcheck.
- APP_URL is not set: Maître does not give a template the Service's address.
