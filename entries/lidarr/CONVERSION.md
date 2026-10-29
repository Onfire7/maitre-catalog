# Conversion of Lidarr

From `Lidarr`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- lidarr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- lidarr: container_name "lidarr" is dropped; Maître names the container, and other containers reach it as "lidarr"
- lidarr: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- lidarr: CasaOS's /DATA/AppData/lidarr/config is the Service volume "config", kept in a Storage Space
- lidarr: CasaOS's shared /DATA/Media/Music is the shared volume "music"; the user picks the folder at install
- lidarr: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /ping.
