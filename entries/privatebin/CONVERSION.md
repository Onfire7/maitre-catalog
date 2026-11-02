# Conversion of Privatebin

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/privatebin/data is the Service volume "data", kept in a Storage Space
- app: CasaOS's /DATA/AppData/privatebin/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/PrivateBin/PrivateBin, PrivateBin's own repository.
- PUID and PGID are dropped: PrivateBin's image runs as nobody and reads neither.
