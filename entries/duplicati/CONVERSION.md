# Conversion of Duplicati

From `Duplicati`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- duplicati: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- duplicati: container_name "duplicati" is dropped; Maître names the container, and other containers reach it as "duplicati"
- duplicati: TZ=Europe/London is replaced by the TZ setting, the Node's time zone unless changed
- duplicati: CasaOS's /DATA/AppData/duplicati/config is the Service volume "config", kept in a Storage Space
- duplicati: CasaOS's shared /DATA/Duplicati/backups is the shared volume "backups"; the user picks the folder at install
- duplicati: CasaOS's shared /DATA/Duplicati/source is the shared volume "source"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
