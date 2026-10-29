# Conversion of Syncthing

From `Syncthing`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- syncthing mounts the Node's own folder /DATA; point it at a Service volume, or keep it and allow it when installing

## Changed for you

Done differently from the Compose file; check they suit the app.

- syncthing: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- syncthing: container_name "syncthing" is dropped; Maître names the container, and other containers reach it as "syncthing"
- syncthing: CasaOS's /DATA/AppData/syncthing/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Edited by hand

After the conversion, for the Catalog:

- The whole of CasaOS's /DATA, mounted at /DATA, is replaced by a shared folder the user picks, mounted at /sync.
