# Conversion of Sonarr

From `Sonarr`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- sonarr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- sonarr: container_name "sonarr" is dropped; Maître names the container, and other containers reach it as "sonarr"
- sonarr: CasaOS's /DATA/AppData/sonarr/config is the Service volume "config", kept in a Storage Space
- sonarr: CasaOS's shared /DATA/Media/TV Shows is the shared volume "tv_shows"; the user picks the folder at install
- sonarr: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /ping.
