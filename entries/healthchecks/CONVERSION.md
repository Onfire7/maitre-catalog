# Conversion of Healthchecks

From `docker-compose.yml`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-healthchecks: SECRET_KEY is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-healthchecks: SUPERUSER_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value
- big-bear-healthchecks: SITE_ROOT=http://[YOUR_CASAOS_IP] holds a placeholder to fill in

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-healthchecks: container_name "big-bear-healthchecks" is dropped; Maître names the container, and other containers reach it as "big-bear-healthchecks"
- big-bear-healthchecks: TZ=Etc/UTC is replaced by the TZ setting, the Node's time zone unless changed
- big-bear-healthchecks: CasaOS's /DATA/AppData/healthchecks/config is the Service volume "config", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/healthchecks/healthchecks, Healthchecks's own repository.
- The administrator's email is a setting, and the administrator's password and the signing key are made up at install; the file wrote them in.
- SITE_ROOT is the Service's address on the home network, http://<name>.local, in place of the file's placeholder, and SITE_NAME is Healthchecks.
- DEBUG is False: the file's True relaxes checks and is for development.
- INTEGRATIONS_ALLOW_PRIVATE_IPS is True, so alerts can go to ntfy, Gotify and other Services on the same Node.
- The empty mail and other settings are gone: each leaves the image's default. Alerts by email need the EMAIL_* values in /config/local_settings.py.
- Port 2525, its listener for pings sent by email, is not published.
- Health is /api/v1/status/.
