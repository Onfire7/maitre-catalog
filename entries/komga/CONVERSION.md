# Conversion of Komga

From `Komga`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- komga: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- komga: container_name "komga" is dropped; Maître names the container, and other containers reach it as "komga"
- komga: CasaOS's /DATA/AppData/komga/config is the Service volume "config", kept in a Storage Space
- komga: CasaOS's /DATA/AppData/komga/data is the Service volume "data", kept in a Storage Space
- komga: the host's /etc/timezone is replaced by the TZ setting, the Node's time zone unless changed
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/gotson/komga, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Its /data, the library, is a shared folder the user picks ("library"), not a folder of its own.
