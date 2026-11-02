# Conversion of Homepage

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- app mounts the Node's own /var/run/docker.sock, which Maître does not support yet (it needs SELinux letting a container use the Node's Podman socket (container_t to container_runtime_t) without turning SELinux off for it, and a warning that says the socket is root on the Node); drop it if the app works without it, or leave the entry out

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "homepage" is dropped; Maître names the container, and other containers reach it as "app"
- app: CasaOS's /DATA/AppData/homepage/config is the Service volume "config", kept in a Storage Space

## Notes

- project: https://github.com/gethomepage/homepage, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The Docker socket mount is dropped: Maître does not support the Podman socket yet (catalog-check says what it needs). Homepage works without it; its automatic container discovery and the Docker widgets do not.
- HOMEPAGE_ALLOWED_HOSTS is *: since version 1.0 Homepage refuses a request whose Host it was not told about, and a Service's page is reached under several names (<name>.local, over Tailscale, a public host).
- Health is /api/healthcheck.
