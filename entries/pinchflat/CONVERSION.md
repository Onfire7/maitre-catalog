# Conversion of Pinchflat

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- pinchflat: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- pinchflat: container_name "pinchflat" is dropped; Maître names the container, and other containers reach it as "pinchflat"
- pinchflat: CasaOS's /DATA/AppData/pinchflat/config is the Service volume "config", kept in a Storage Space
- pinchflat: CasaOS's shared /DATA/Media/Downloads is the shared volume "downloads"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- project: https://github.com/kieraneglin/pinchflat, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The image stays at the latest tag, pinned by digest: the project publishes no image tag for its releases after v2025.6.6, and this build is one commit after release v2025.9.26 (yt-dlp for arm64), so the version is 2025.9.26.
- The downloads volume is marked large, for a Storage Space with room.
- Health is /healthcheck.
