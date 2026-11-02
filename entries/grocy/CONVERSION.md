# Conversion of Grocy

From `grocy`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/grocy/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The page is on port 80, the port LinuxServer's image listens on: Big Bear's file had the two sides of its mapping the wrong way round (target 9283, published 80), so the entry proxied to a port nothing answered on and every open was a 502 (fixed 2026-11-02).
