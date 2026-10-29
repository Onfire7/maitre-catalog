# Conversion of Calibre-web

From `Calibre-web`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- calibre-web: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- calibre-web: container_name "calibre-web" is dropped; Maître names the container, and other containers reach it as "calibre-web"
- calibre-web: CasaOS's /DATA/AppData/calibre-web/config is the Service volume "config", kept in a Storage Space
- calibre-web: CasaOS's shared /DATA/Media/Books is the shared volume "books"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
