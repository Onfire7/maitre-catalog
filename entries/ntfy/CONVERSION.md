# Conversion of Ntfy.sh

From `ntfysh`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: TZ=UTC is replaced by the TZ setting, the Node's time zone unless changed
- app: CasaOS's /DATA/AppData/ntfy/cache is the Service volume "cache", kept in a Storage Space
- app: CasaOS's /DATA/AppData/ntfy/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Reachable from anywhere by default (exposure: remote), so the phone app gets notifications away from home.
- Health is its own /v1/health.
