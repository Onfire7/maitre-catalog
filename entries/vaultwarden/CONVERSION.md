# Conversion of Vaultwarden

From `Vaultwarden`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- vaultwarden: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- vaultwarden: container_name "vaultwarden" is dropped; Maître names the container, and other containers reach it as "vaultwarden"
- vaultwarden: CasaOS's /DATA/AppData/vaultwarden/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- Reachable from anywhere by default (exposure: remote): browsers open its vault only over HTTPS, which Tailscale gives.
