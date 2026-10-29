# Conversion of Memos

From `Memos`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- memos: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- memos: container_name "memos" is dropped; Maître names the container, and other containers reach it as "memos"
- memos: CasaOS's /DATA/AppData/memos/memos is the Service volume "memos", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- PUID and PGID are dropped: the Memos image does not read them.
- Health is its own /healthz.
