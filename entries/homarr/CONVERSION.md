# Conversion of Homarr v2

From `homarr-v2`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-homarr-v2 mounts the Node's own /var/run/docker.sock, which Maître does not support yet (it needs SELinux letting a container use the Node's Podman socket (container_t to container_runtime_t) without turning SELinux off for it, and a warning that says the socket is root on the Node); drop it if the app works without it, or leave the entry out

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-homarr-v2: container_name "big-bear-homarr-v2" is dropped; Maître names the container, and other containers reach it as "big-bear-homarr-v2"
- big-bear-homarr-v2: CasaOS's /DATA/AppData/homarr/appdata is the Service volume "appdata", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/homarr-labs/homarr, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- SECRET_ENCRYPTION_KEY, empty in the file, is made up at install as Homarr asks: 32 random bytes in hex.
- The Docker socket mount is dropped: Maître does not support the Podman socket yet (catalog-check says what it needs). Homarr works without it; its container view does not.
- Health is /api/health/live.
