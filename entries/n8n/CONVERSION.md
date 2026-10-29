# Conversion of n8n

From `N8n`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- n8n: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- n8n: container_name "n8n" is dropped; Maître names the container, and other containers reach it as "n8n"
- n8n: CasaOS's /DATA/AppData/n8n is the Service volume "n8n", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/n8n-io/n8n, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /healthz.
