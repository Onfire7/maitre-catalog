# Conversion of Bazarr

From `Bazarr`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- bazarr: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- bazarr: container_name "bazarr" is dropped; Maître names the container, and other containers reach it as "bazarr"
- bazarr: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- bazarr: CasaOS's shared /DATA/Media/Movies is the shared volume "movies"; the user picks the folder at install
- bazarr: CasaOS's shared /DATA/Media/TV Shows is the shared volume "tv_shows"; the user picks the folder at install
- bazarr: CasaOS's /DATA/AppData/bazarr/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
