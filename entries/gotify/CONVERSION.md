# Conversion of Gotify

From `gotify`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- app: GOTIFY_DEFAULTUSER_PASS is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/gotify/data is the Service volume "data", kept in a Storage Space

## Notes

- project: https://github.com/gotify/server, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The admin password is made up at install (ADMIN_PASSWORD), not the one written into the file.
- Reachable from anywhere by default (exposure: remote), so the phone app gets messages away from home.
- Health is its own /health.
