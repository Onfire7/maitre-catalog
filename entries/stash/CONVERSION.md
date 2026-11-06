# Conversion of Stash

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- Write the entry's summary and description

## Changed for you

Done differently from the Compose file; check they suit the app.

- stash: container_name "stash" is dropped; Maître names the container, and other containers reach it as "stash"
- stash: TZ=Etc/UTC is replaced by the TZ setting, the Node's time zone unless changed
- stash: the folder ./config is the Service volume "config", kept in a Storage Space
- stash: the folder ./data is the Service volume "data", kept in a Storage Space
- stash: the folder ./metadata is the Service volume "metadata", kept in a Storage Space
- stash: the folder ./cache is the Service volume "cache", kept in a Storage Space
- stash: the folder ./blobs is the Service volume "blobs", kept in a Storage Space
- stash: the folder ./generated is the Service volume "generated", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/stashapp/stash, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are in the Catalog's words, with the setup choices that match the folders this Service mounts.
- The image is pinned to the v0.32.0 tag, the release the Compose file was taken from. It has the same digest `latest` had.
- The Compose file's `./data` is "Point this at your collection", so it is the shared volume "collection", a folder the person picks (`:z`), sized large. Generated content, which holds transcodes and previews, is sized large and blobs medium.
- The category is media.
- Health is `/`. Stash answers `/healthz` with its web app's catch-all page, which proves no more than `/` does.
