# Conversion of Grafana

From `Grafana`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- grafana: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- grafana: container_name "grafana" is dropped; Maître names the container, and other containers reach it as "grafana"
- grafana: CasaOS's /DATA/AppData/grafana/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/grafana/grafana, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The image is the newest plain release, 13.3.0, instead of 13.0.1-security-01, whose suffix would keep `maitre catalog outdated` from following new releases.
- Health is its own /api/health.
