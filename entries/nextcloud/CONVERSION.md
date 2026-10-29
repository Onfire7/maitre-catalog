# Conversion of Nextcloud

From `Nextcloud`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- nextcloud: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- nextcloud: container_name "nextcloud" is dropped; Maître names the container, and other containers reach it as "nextcloud"
- nextcloud: CasaOS's /DATA/AppData/nextcloud/var/www/html is the Service volume "html", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The published port 10443:443 is removed: the image serves only port 80, which Caddy serves.
