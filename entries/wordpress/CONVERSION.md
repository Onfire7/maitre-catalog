# Conversion of WordPress v7

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into app's WORDPRESS_DB_PASSWORD and db's MYSQL_PASSWORD and db's MYSQL_ROOT_PASSWORD is the setting WORDPRESS_DB_PASSWORD, made up at install
- app: CasaOS's /DATA/AppData/wordpress/html is the Service volume "html", kept in a Storage Space
- db: CasaOS's /DATA/AppData/wordpress/mysql is the Service volume "mysql", kept in a Storage Space

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The name is WordPress, not Big Bear's WordPress v7; the summary and description are shorter, in the Catalog's words.
- project: https://github.com/WordPress/WordPress, WordPress's own repository; the official image carries no source label.
- The database user is wordpress, not casaos, and the file's one password casaos served it and the database's root; the user's password (DB_PASSWORD) and the root's (DB_ROOT_PASSWORD) are settings made up at install.
- Health is /wp-login.php.
