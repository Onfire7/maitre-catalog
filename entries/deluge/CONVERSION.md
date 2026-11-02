# Conversion of Deluge

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- deluge mounts the Node's own folder /DATA; point it at a Service volume, or keep it and declare it under grants: with why

## Changed for you

Done differently from the Compose file; check they suit the app.

- deluge: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- deluge: container_name "deluge" is dropped; Maître names the container, and other containers reach it as "deluge"
- deluge: CasaOS's /DATA/AppData/deluge/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/deluge-torrent/deluge, Deluge's own repository.
- The file mounted the whole of CasaOS's /DATA; Deluge gets the shared downloads volume at /downloads, where the image's default download location is.
- Deluge's web password is deluge until changed on its page; it is kept in its own hashed config, so no setting can make one up at install.
