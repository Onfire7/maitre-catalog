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
entries/<id>/icon.svg        copied from an icon pack; see FORMAT.md
entries/<id>/compose.yaml    a converted entry's source, as it came
entries/<id>/CONVERSION.md   what its conversion and later hand edits changed
popularity.json              each entry's project stars, the Catalog page's sort; see FORMAT.md
NOTICE                       generated: what the Catalog carries of other projects
LICENSES/                    those projects' licence texts
index.json                   generated: `maitre catalog-index entries > index.json`
```

Images are pinned by digest in the manifest. Updating an entry means
changing the digest; the agent's Service auto-update follows the index.
`maitre catalog outdated entries` lists the images with a newer tag in their
series or rebuilt under the same tag, and `--write` repins them. Maître
Server's CI runs it every week and opens a pull request here with the new
pins, and one there that boots them.

## Your own Catalog

A Catalog of your own is a folder, or a git repository, laid out as this one
is: `entries/<id>/` beside an optional README. Add it from the Console's
Catalog page (Catalogs, then Add a folder or Add a git repository). Every
Console of the Fleet lists it; each reads a git Catalog from its own clone of
the branch you name, and a folder only on the computer it is on. Entries that
do not load are listed with why, and the rest still show. To a folder
Catalog the Console can add a Compose file, converted by `maitre catalog add`.
