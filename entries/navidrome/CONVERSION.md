# Conversion of Navidrome

From `Navidrome`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- navidrome: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- navidrome: container_name "navidrome" is dropped; Maître names the container, and other containers reach it as "navidrome"
- navidrome: CasaOS's /DATA/AppData/navidrome/data is the Service volume "data", kept in a Storage Space
- navidrome: CasaOS's shared /DATA/Media/Music is the shared volume "music"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- Reachable from anywhere by default (exposure: remote), as Jellyfin is, for its phone apps.
