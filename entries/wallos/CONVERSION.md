# Conversion of Wallos

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-wallos: container_name "big-bear-wallos" is dropped; Maître names the container, and other containers reach it as "big-bear-wallos"
- big-bear-wallos: TZ=UTC is replaced by the TZ setting, the Node's time zone unless changed
- big-bear-wallos: CasaOS's /DATA/AppData/wallos/db is the Service volume "db", kept in a Storage Space
- big-bear-wallos: CasaOS's /DATA/AppData/wallos/logos is the Service volume "logos", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/ellite/Wallos, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
