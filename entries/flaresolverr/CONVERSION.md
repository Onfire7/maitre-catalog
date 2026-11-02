# Conversion of FlareSolverr

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- Write the entry's summary and description

## Changed for you

Done differently from the Compose file; check they suit the app.

- flaresolverr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- flaresolverr: deploy.resources reservations (CPUWeight=) are dropped; Maître sets no reservations
- flaresolverr: container_name "flaresolverr" is dropped; Maître names the container, and other containers reach it as "flaresolverr"
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- project: https://github.com/FlareSolverr/FlareSolverr, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are written: the file had none.
- PUID and PGID are dropped: FlareSolverr's image is not LinuxServer's and reads neither.
- Health is /health.
