# Conversion of Tandoor

From `tandoor`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-tandoor: SECRET_KEY is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- The password written into big-bear-tandoor's POSTGRES_PASSWORD and big-bear-tandoor-db's POSTGRES_PASSWORD is the setting POSTGRES_PASSWORD, made up at install
- big-bear-tandoor: container_name "big-bear-tandoor" is dropped; Maître names the container, and other containers reach it as "big-bear-tandoor"
- big-bear-tandoor: CasaOS's /DATA/AppData/tandoor/staticfiles is the Service volume "staticfiles", kept in a Storage Space
- big-bear-tandoor: CasaOS's /DATA/AppData/tandoor/mediafiles is the Service volume "mediafiles", kept in a Storage Space
- big-bear-tandoor-db: container_name "big-bear-tandoor-db" is dropped; Maître names the container, and other containers reach it as "big-bear-tandoor-db"
- big-bear-tandoor-db: CasaOS's /DATA/AppData/tandoor/postgresql is the Service volume "postgresql", kept in a Storage Space
- big-bear-tandoor waits for big-bear-tandoor-db's health check through Notify=healthy, instead of compose2quadlet's polling loop, which would run on the Node
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/TandoorRecipes/recipes, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The components are named app and db, not after Big Bear's containers; the app reaches the database at db.
- SECRET_KEY is made up at install, not the one written into the file.
