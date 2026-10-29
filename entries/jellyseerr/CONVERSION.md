# Conversion of Jellyseerr

From `Jellyseerr`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- jellyseerr: [Service] MemoryMax= (from x-systemd) is not carried over; it would run on the Node itself

## Changed for you

Done differently from the Compose file; check they suit the app.

- jellyseerr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- jellyseerr: deploy.resources reservations (CPUWeight=) are dropped; Maître sets no reservations
- jellyseerr: CasaOS's /DATA/AppData/jellyseerr is the Service volume "jellyseerr", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/fallenbagel/jellyseerr, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- x-systemd's MemoryMax= is dropped: it would be a line in [Service], which runs on the Node itself.
- LOG_LEVEL is info, not debug.
- Health is /api/v1/status.
