# Conversion of Ghost

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into app's database__connection__password and db's MYSQL_PASSWORD and db's MYSQL_ROOT_PASSWORD is the setting database__connection__password, made up at install
- app: container_name "big-bear-ghost" is dropped; Maître names the container, and other containers reach it as "app"
- app: CasaOS's /DATA/AppData/ghost/content is the Service volume "content", kept in a Storage Space
- db: container_name "big-bear-ghost-db" is dropped; Maître names the container, and other containers reach it as "db"
- db: CasaOS's /DATA/AppData/ghost/mysql is the Service volume "mysql", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/TryGhost/Ghost, Ghost's own repository; the official image carries no source label.
- The version is 6.73.0: the tag's -alpine names the image's base, not Ghost's version.
- The file's one password casaos served the app, the database user and the database's root; the user's password (DB_PASSWORD) and the root's (DB_ROOT_PASSWORD) are settings made up at install.
- url is the Service's address on the home network, http://<name>.local, instead of localhost: Ghost builds its links and redirects to its admin from it, so a Ghost reached from away or at a public host needs this changed to that address.
- Health is /ghost/api/admin/site/, which answers without signing in.
