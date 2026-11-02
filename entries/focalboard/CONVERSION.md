# Conversion of Focalboard

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "big-bear-focalboard" is dropped; Maître names the container, and other containers reach it as "app"
- app: CasaOS's /DATA/AppData/focalboard/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/mattermost-community/focalboard, where Mattermost moved the project; its image is still published as mattermost/focalboard.
- Health is /hello.
- Its own volumes mount with Podman's U option: the image runs as a user other than root, and the Node makes a Service's folders as root, so without it the app could not write them (seen on a Node with Vikunja, 2026-11-02).
