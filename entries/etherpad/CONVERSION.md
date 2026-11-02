# Conversion of Etherpad

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- etherpad: ADMIN_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- etherpad: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- etherpad: container_name "etherpad" is dropped; Maître names the container, and other containers reach it as "etherpad"
- etherpad: CasaOS's /DATA/AppData/etherpad/var is the Service volume "var", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/ether/etherpad, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- ADMIN_PASSWORD is a setting made up at install, not the admin written into the file.
- The default pad text no longer welcomes you to CasaOS.
- Health is /health, the same the file's own check asked.
- Its own volumes mount with Podman's U option: the image runs as a user other than root, and the Node makes a Service's folders as root, so without it the app could not write them (seen on a Node with Vikunja, 2026-11-02).
