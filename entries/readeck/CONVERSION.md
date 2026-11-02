# Conversion of Readeck

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-readeck: container_name "big-bear-readeck" is dropped; Maître names the container, and other containers reach it as "big-bear-readeck"
- big-bear-readeck: CasaOS's /DATA/AppData/readeck/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://codeberg.org/readeck/readeck, Readeck's own repository.
- Health is /, which shows the sign-in page; Readeck's own healthcheck command only tries a TCP connection.
- The image is 0.23.5, not the 0.22.3 the file pinned: Codeberg keeps only a project's last few tags, and 0.22.3 and its digest are gone from the registry, so the pin could not be pulled.
