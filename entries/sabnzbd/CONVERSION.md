# Conversion of Sabnzbd

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- sabnzbd: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- sabnzbd: container_name "sabnzbd" is dropped; Maître names the container, and other containers reach it as "sabnzbd"
- sabnzbd: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- sabnzbd: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- sabnzbd: CasaOS's /DATA/AppData/sabnzbd/config is the Service volume "config", kept in a Storage Space
- sabnzbd: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/sabnzbd/sabnzbd, SABnzbd's own repository.
- The file mounted the one Downloads folder at both /downloads and /incomplete-downloads; finished downloads go to the shared downloads volume and the half-done ones to a volume of their own, as the image's defaults expect.
- SABnzbd refuses a page request whose Host it does not know; the Node's proxy always presents <name>.local, which it allows as an mDNS name, so no host_whitelist entry is needed.
- Health is /api?mode=version, which answers without the API key.
