# Conversion of FreshRSS

From `FreshRSS`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- freshrss: container_name "freshrss" is dropped; Maître names the container, and other containers reach it as "freshrss"
- freshrss: TZ= is replaced by the TZ setting, the Node's time zone unless changed
- freshrss: CasaOS's /DATA/AppData/freshrss/data is the Service volume "data", kept in a Storage Space
- freshrss: CasaOS's /DATA/AppData/freshrss/extensions is the Service volume "extensions", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
