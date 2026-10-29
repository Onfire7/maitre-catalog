# Conversion of PhotoPrism

From `PhotoPrism`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- photoprism: PHOTOPRISM_ADMIN_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- photoprism: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- photoprism: container_name "photoprism" is dropped; Maître names the container, and other containers reach it as "photoprism"
- photoprism: CasaOS's /DATA/AppData/photoprism/photoprism/storage is the Service volume "storage", kept in a Storage Space
- photoprism: CasaOS's shared /DATA/Gallery is the shared volume "gallery"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/photoprism/photoprism, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The admin password is made up at install (ADMIN_PASSWORD), not the one written into the file.
- Health is /api/v1/status.
