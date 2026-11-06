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
- `GROCY_BASE_URL` is `//`, so every link, stylesheet and image Grocy writes is a path from the root. At its default of `/`, Grocy builds each one from the Host the request arrived with, and the Node's proxy sends `grocy.local`, a name the Console cannot reach, so pages loaded without their styles, scripts or images. Grocy uses any value other than `/` as a prefix with its trailing slashes removed, and `//` is the shortest such value that leaves nothing. An empty value would mean the same to Grocy, but LinuxServer's s6 init drops empty variables before PHP starts (fixed 2026-11-06).
