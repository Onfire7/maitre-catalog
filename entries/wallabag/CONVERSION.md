# Conversion of Wallabag

From `Wallabag`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- wallabag: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- wallabag: container_name "wallabag" is dropped; Maître names the container, and other containers reach it as "wallabag"
- wallabag: CasaOS's /DATA/AppData/wallabag/images is the Service volume "images", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Its database is kept: /var/www/wallabag/data is the Service volume "data", which the file left inside the container.
- SYMFONY__ENV__DOMAIN_NAME is the Service's address on the home network, http://<name>.local, instead of the file's placeholder.
- The project is wallabag/wallabag; the image names its packaging repository.
