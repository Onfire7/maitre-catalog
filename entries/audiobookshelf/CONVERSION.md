# Conversion of Audiobookshelf

From `Audiobookshelf`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- audiobookshelf: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- audiobookshelf: container_name "audiobookshelf" is dropped; Maître names the container, and other containers reach it as "audiobookshelf"
- audiobookshelf: CasaOS's shared /DATA/Media/Audiobooks is the shared volume "audiobooks"; the user picks the folder at install
- audiobookshelf: CasaOS's shared /DATA/Media/Podcasts is the shared volume "podcasts"; the user picks the folder at install
- audiobookshelf: CasaOS's /DATA/AppData/audiobookshelf/config is the Service volume "config", kept in a Storage Space
- audiobookshelf: CasaOS's /DATA/AppData/audiobookshelf/metadata is the Service volume "metadata", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Reachable from anywhere by default (exposure: remote), as Jellyfin is, for its phone apps.
- Health is its own /healthcheck.
