# Conversion of Pairdrop

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/pairdrop/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/schlagmichdoch/PairDrop, PairDrop's own repository.
- The empty RATE_LIMIT, WS_FALLBACK, RTC_CONFIG and DEBUG_MODE are gone: empty, each leaves the image's default.
