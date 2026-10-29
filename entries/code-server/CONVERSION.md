# Conversion of Code Server

From `code-server`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- app: PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value
- app: SUDO_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "code-server" is dropped; Maître names the container, and other containers reach it as "app"
- app: TZ=UTC is replaced by the TZ setting, the Node's time zone unless changed
- app: CasaOS's /DATA/AppData/code-server/config is the Service volume "config", kept in a Storage Space
- app: CasaOS's /DATA/AppData/code-server/projects is the Service volume "projects", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- PASSWORD and SUDO_PASSWORD, written into the file, are made up at install.
- Health is its own /healthz.
