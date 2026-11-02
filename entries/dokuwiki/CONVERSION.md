# Conversion of Dokuwiki

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/dokuwiki/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/dokuwiki/dokuwiki, DokuWiki's own repository.
- The version is DokuWiki's release name 2026-07-14c, which LinuxServer tags as version-2026-07-14c.
- Port 443, the container's own HTTPS with a self-signed certificate, is not published: the Node's proxy fronts the Service.
