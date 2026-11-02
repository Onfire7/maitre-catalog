# Conversion of Hedgedoc

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- The setting CMD_ALLOW_ORIGIN has no default; give one, or it is asked for empty at install
- The setting CMD_DB_DIALECT has no default; give one, or it is asked for empty at install
- The setting CMD_DOMAIN has no default; give one, or it is asked for empty at install
- The setting CMD_PORT has no default; give one, or it is asked for empty at install
- The setting CMD_PROTOCOL_USESSL has no default; give one, or it is asked for empty at install
- The setting CMD_URL_ADDPORT has no default; give one, or it is asked for empty at install
- The setting DB_HOST has no default; give one, or it is asked for empty at install
- The setting DB_NAME has no default; give one, or it is asked for empty at install
- The setting DB_PORT has no default; give one, or it is asked for empty at install
- The setting DB_USER has no default; give one, or it is asked for empty at install

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/hedgedoc/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- DB_PASS is made up at install
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/hedgedoc/hedgedoc, HedgeDoc's own repository.
- The file left a database host, port, user, password and name to fill in; with none given, LinuxServer's image uses SQLite at /config/hedgedoc.sqlite, which suits a home, so those settings and CMD_DB_DIALECT are gone.
- CMD_DOMAIN and CMD_ALLOW_ORIGIN are the Service's name on the home network, <name>.local, with CMD_URL_ADDPORT and CMD_PROTOCOL_USESSL false: the file left them to fill in, and HedgeDoc builds its links and allows its live connection from them. CMD_PORT is gone; 3000 is the image's default.
- Health is /status.
