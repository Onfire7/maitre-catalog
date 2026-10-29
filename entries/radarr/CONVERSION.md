# Conversion of Radarr

From `Radarr`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- radarr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- radarr: container_name "radarr" is dropped; Maître names the container, and other containers reach it as "radarr"
- radarr: CasaOS's /DATA/AppData/radarr/config is the Service volume "config", kept in a Storage Space
- radarr: CasaOS's shared /DATA/Media/Movies is the shared volume "movies"; the user picks the folder at install
- radarr: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /ping.
