# Conversion of Umami

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- app: APP_SECRET is written into the file; make it a setting (default: generate) unless the app relies on this value
- db: POSTGRES_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- db: CasaOS's /DATA/AppData/umami/pgdata is the Service volume "pgdata", kept in a Storage Space
- app waits for db's health check through Notify=healthy, instead of compose2quadlet's polling loop, which would run on the Node
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The image is tagged 3.4.1, the same image Big Bear's postgresql-latest pointed at (one digest), so the entry has a version to check against; since version 3 the project tags images by version alone.
- project: https://github.com/umami-software/umami, Umami's own repository; the image carries no source label.
- APP_SECRET and the database password, written into the file, are settings made up at install.
- Health is /api/heartbeat.
