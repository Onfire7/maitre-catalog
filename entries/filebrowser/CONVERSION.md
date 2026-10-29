# Conversion of Filebrowser

From `filebrowser`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-filebrowser: container_name "big-bear-filebrowser" is dropped; Maître names the container, and other containers reach it as "big-bear-filebrowser"
- big-bear-filebrowser: CasaOS's shared /DATA/AppData is the shared volume "appdata"; the user picks the folder at install
- big-bear-filebrowser: CasaOS's shared /DATA/Documents is the shared volume "documents"; the user picks the folder at install
- big-bear-filebrowser: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- big-bear-filebrowser: CasaOS's shared /DATA/Gallery is the shared volume "gallery"; the user picks the folder at install
- big-bear-filebrowser: CasaOS's shared /DATA/media is the shared volume "media"; the user picks the folder at install
- big-bear-filebrowser: CasaOS's /DATA/AppData/filebrowser/data/db is the Service volume "db", kept in a Storage Space
- big-bear-filebrowser: CasaOS's /DATA/AppData/filebrowser/data/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/filebrowser/filebrowser, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /health.
