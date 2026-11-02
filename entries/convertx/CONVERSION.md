# Conversion of ConvertX

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- convertx: JWT_SECRET is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- convertx: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- convertx: container_name "convertx" is dropped; Maître names the container, and other containers reach it as "convertx"
- convertx: CasaOS's /DATA/AppData/convertx/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/C4illin/ConvertX, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- JWT_SECRET is made up at install; the file wrote it in.
- HTTP_ALLOWED stays true: the Node's proxy speaks plain HTTP to it.
