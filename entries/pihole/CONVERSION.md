# Conversion of Pi-hole

From `Pihole`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- pihole: FTLCONF_webserver_api_password is written into the file; make it a setting (default: generate) unless the app relies on this value
- pihole asks for AddCapability=NET_ADMIN, which a Trusted Device must allow at install; keep it only if the app needs it

## Changed for you

Done differently from the Compose file; check they suit the app.

- pihole: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- pihole: container_name "pihole" is dropped; Maître names the container, and other containers reach it as "pihole"
- pihole: CasaOS's /DATA/AppData/pihole/etc/pihole/ is the Service volume "pihole", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The web interface password, fixed at "casaos" in the file, is the setting WEB_PASSWORD, made up at install.
- AddCapability=NET_ADMIN is removed: Pi-hole needs it only for its own DHCP server, which the entry does not offer; DNS works without it.
- The HTTPS port 8443 is removed; Caddy serves the web interface.
- Marked infrastructure, like AdGuard Home: DNS starts before the network is up and its Node keeps a fixed address.
