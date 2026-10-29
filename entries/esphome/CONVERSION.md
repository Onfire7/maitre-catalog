# Conversion of ESPHome

From `ESPHome`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- esphome asks for Network=host, which a Trusted Device must allow at install; keep it only if the app needs it, and declare it under grants: with why (optional: if the app works without it)

## Changed for you

Done differently from the Compose file; check they suit the app.

- esphome: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- esphome: container_name "esphome" is dropped; Maître names the container, and other containers reach it as "esphome"
- esphome: CasaOS's /DATA/AppData/esphome/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/esphome/esphome, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The Node's own network is an optional feature (discovery); without it devices are checked by ping (ESPHOME_DASHBOARD_USE_PING=true).
- Health is its dashboard at /.
