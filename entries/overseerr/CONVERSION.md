# Conversion of Overseerr

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- overseerr: container_name "overseerr" is dropped; Maître names the container, and other containers reach it as "overseerr"
- overseerr: CasaOS's /DATA/AppData/overseerr/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/sct/overseerr, Overseerr's own repository; LinuxServer's image carries no source label.
- Health is /api/v1/status.
