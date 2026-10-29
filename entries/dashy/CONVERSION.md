# Conversion of Dashy v4

From `dashy-v4`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-dashy-v4: container_name "big-bear-dashy-v4" is dropped; Maître names the container, and other containers reach it as "big-bear-dashy-v4"
- big-bear-dashy-v4: CasaOS's /DATA/AppData/dashy/user-data is the Service volume "user_data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/lissy93/dashy, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
