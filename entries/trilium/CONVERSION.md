# Conversion of Trilium

From `Trilium`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- trilium: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- trilium: container_name "trilium" is dropped; Maître names the container, and other containers reach it as "trilium"
- trilium: CasaOS's /DATA/AppData/trilium is the Service volume "trilium", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/TriliumNext/Trilium, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Health is its own /api/health-check.
