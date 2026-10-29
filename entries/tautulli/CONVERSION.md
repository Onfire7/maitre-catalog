# Conversion of Tautulli

From `Tautulli`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- tautulli: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- tautulli: container_name "tautulli" is dropped; Maître names the container, and other containers reach it as "tautulli"
- tautulli: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- tautulli: CasaOS's /DATA/AppData/tautulli/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
