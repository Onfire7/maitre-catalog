# Conversion of Kavita

From `Kavita`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- kavita: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- kavita: container_name "kavita" is dropped; Maître names the container, and other containers reach it as "kavita"
- kavita: CasaOS's /DATA/AppData/kavita/config is the Service volume "config", kept in a Storage Space
- kavita: CasaOS's shared /DATA/Media/Manga is the shared volume "manga"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The version is the tag's, 0.9.0.2.
- Health is its own /api/health.
