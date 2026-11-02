# Conversion of Planka v2

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-planka-v2: DEFAULT_ADMIN_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-planka-v2: SECRET_KEY is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-planka-v2: BASE_URL=http://[YOUR_CASAOS_LAN_IP]:3001 holds a placeholder to fill in

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-planka-v2: container_name "big-bear-planka-v2" is dropped; Maître names the container, and other containers reach it as "big-bear-planka-v2"
- big-bear-planka-v2: CasaOS's /DATA/AppData/planka/data is the Service volume "data", kept in a Storage Space
- big-bear-planka-v2: CasaOS's /DATA/AppData/planka/background-images is the Service volume "background_images", kept in a Storage Space
- big-bear-planka-v2: CasaOS's /DATA/AppData/planka/user-avatars is the Service volume "user_avatars", kept in a Storage Space
- big-bear-planka-v2: CasaOS's /DATA/AppData/planka/project-background-images is the Service volume "project_background_images", kept in a Storage Space
- big-bear-planka-v2: CasaOS's /DATA/AppData/planka/attachments is the Service volume "attachments", kept in a Storage Space
- big-bear-planka-v2-postgres: CasaOS's /DATA/AppData/planka/postgresql is the Service volume "postgresql", kept in a Storage Space
- big-bear-planka-v2 waits for big-bear-planka-v2-postgres's health check through Notify=healthy, instead of compose2quadlet's polling loop, which would run on the Node
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/plankanban/planka, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The name is Planka, not Big Bear's Planka v2; the summary and description are shorter, in the Catalog's words.
- The components are named app and db, not after Big Bear's containers; the app reaches the database at db.
- The database asks for a password (DB_PASSWORD, made up at install) instead of trusting every connection (POSTGRES_HOST_AUTH_METHOD=trust).
- SECRET_KEY is made up at install as Planka asks: 64 random bytes in hex.
- The demo administrator (demo@demo.demo, password demo) is replaced by settings: email, username and name asked at install, and a password made up at install.
- BASE_URL is the Service's address on the home network, http://<name>.local, instead of the file's placeholder; Planka builds the links in its emails and attachments from it.
- Health is /.
