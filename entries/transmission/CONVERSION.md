# Conversion of Transmission

From `Transmission`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- transmission: PASS is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- transmission: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- transmission: container_name "transmission" is dropped; Maître names the container, and other containers reach it as "transmission"
- transmission: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- transmission: CasaOS's /DATA/AppData/transmission/config is the Service volume "config", kept in a Storage Space
- transmission: CasaOS's shared /DATA/Downloads is the shared volume "downloads"; the user picks the folder at install
- transmission: CasaOS's shared /DATA/Downloads/watch is the shared volume "watch"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Its web page's login is admin with a password made up at install, not the user and password written into the file.
