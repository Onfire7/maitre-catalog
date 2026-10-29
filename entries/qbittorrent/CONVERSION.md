# Conversion of qBittorrent

From `qBittorrent`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- qbittorrent mounts the Node's own folder /DATA; point it at a Service volume, or keep it and allow it when installing

## Changed for you

Done differently from the Compose file; check they suit the app.

- qbittorrent: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- qbittorrent: container_name "qbittorrent" is dropped; Maître names the container, and other containers reach it as "qbittorrent"
- qbittorrent: CasaOS's /DATA/AppData/qbittorrent/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- project: https://github.com/hotio/qbittorrent, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The whole of CasaOS's /DATA is replaced by a shared folder the user picks, mounted at /downloads, as Sonarr and Radarr have it.
- The project is qbittorrent/qBittorrent; the image is hotio's package of it.
