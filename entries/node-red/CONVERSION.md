# Conversion of Node-RED

From `Node-RED`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- node-red asks for Network=host, which a Trusted Device must allow at install; keep it only if the app needs it, and declare it under grants: with why (optional: if the app works without it)

## Changed for you

Done differently from the Compose file; check they suit the app.

- node-red: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- node-red: container_name "node-red" is dropped; Maître names the container, and other containers reach it as "node-red"
- node-red: CasaOS's /DATA/AppData/node-red/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- On its own network instead of the Node's (Network=host dropped): Node-RED reaches MQTT, Home Assistant and web services by address, and needs no grant.
- Health is its editor at /.
