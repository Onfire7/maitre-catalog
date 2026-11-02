# Conversion of Lychee

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- The setting APP_NAME has no default; give one, or it is asked for empty at install
- The setting APP_URL has no default; give one, or it is asked for empty at install
- The setting DB_CONNECTION has no default; give one, or it is asked for empty at install
- The setting DB_DATABASE has no default; give one, or it is asked for empty at install
- The setting DB_HOST has no default; give one, or it is asked for empty at install
- The setting DB_PORT has no default; give one, or it is asked for empty at install
- The setting DB_USERNAME has no default; give one, or it is asked for empty at install
- The setting TRUSTED_PROXIES has no default; give one, or it is asked for empty at install

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/lychee/config is the Service volume "config", kept in a Storage Space
- app: CasaOS's /DATA/AppData/lychee/pictures is the Service volume "pictures", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- DB_PASSWORD is made up at install
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/LycheeOrg/Lychee, Lychee's own repository.
- The icon is Lychee's own logo from its repository (MIT), since the one in dashboard-icons is a PNG over the Catalog's size limit and selfh.st has none.
- The file left the database to fill in; DB_CONNECTION is sqlite, which LinuxServer's image keeps at /config/database.sqlite, so the host, port, user, password and name settings are gone.
- APP_NAME is Lychee, APP_URL the Service's address on the home network, http://<name>.local, and TRUSTED_PROXIES * since the only way to it is the Node's proxy.
- The pictures volume is marked large, for a Storage Space with room.
