# Conversion of Draw.io

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: container_name "drawio" is dropped; Maître names the container, and other containers reach it as "app"
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/jgraph/drawio, draw.io's own repository.
