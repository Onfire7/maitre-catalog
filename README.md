# Maître Catalog

The curated list of Services a Maître Fleet can install. MIT licensed so
anyone can fork, add entries, or run their own Catalog. Maître Server
(https://github.com/Onfire7/maitre-de-serveur) includes this repository as a
git submodule and bakes the generated index into its image.

## Layout

```
entries/<id>/manifest.yaml   what the Console shows and asks; see FORMAT.md
entries/<id>/<id>.container  Podman Quadlet template the agent renders
entries/<id>/<name>.container  one per component, in an entry of several
entries/<id>/<name>.volume   the bundle's own volumes, if it has any
index.json                   generated: `maitre catalog-index entries > index.json`
```

Images are pinned by digest in the manifest. Updating an entry means
changing the digest; the agent's Service auto-update follows the index.
