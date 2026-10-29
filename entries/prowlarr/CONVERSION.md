# Conversion of Prowlarr

From `Prowlarr`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- prowlarr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- prowlarr: container_name "prowlarr" is dropped; Maître names the container, and other containers reach it as "prowlarr"
- prowlarr: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- prowlarr: CasaOS's /DATA/AppData/prowlarr/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /ping.
