# Conversion of Wikijs

From `wikijs`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- The setting DB_HOST has no default; give one, or it is asked for empty at install
- The setting DB_NAME has no default; give one, or it is asked for empty at install
- The setting DB_PORT has no default; give one, or it is asked for empty at install
- The setting DB_TYPE has no default; give one, or it is asked for empty at install
- The setting DB_USER has no default; give one, or it is asked for empty at install

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/wikijs/config is the Service volume "config", kept in a Storage Space
- app: CasaOS's /DATA/AppData/wikijs/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- DB_PASS is made up at install
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- It keeps its pages in SQLite (DB_TYPE=sqlite, in its config volume, where the image keeps it) instead of asking for a database server it does not ship with.
- Health is its own /healthz.
