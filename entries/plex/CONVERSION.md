# Conversion of Plex

From `Plex`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- plex asks for AddDevice=/dev/dri:/dev/dri:rwm, which a Trusted Device must allow at install; keep it only if the app needs it, and declare it under grants: with why (optional: if the app works without it)
- plex asks for AddDevice=/dev/dvb:/dev/dvb:rwm, which Maître does not support yet (it needs SELinux letting a container use the device (container-selinux's container_use_devices boolean, off on Fedora, or a narrower rule) set in the Node image, checked on a Node with the device plugged in); find another way, or leave the entry out
- plex asks for Network=host, which a Trusted Device must allow at install; keep it only if the app needs it, and declare it under grants: with why (optional: if the app works without it)

## Changed for you

Done differently from the Compose file; check they suit the app.

- plex: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- plex: container_name "plex" is dropped; Maître names the container, and other containers reach it as "plex"
- plex: CasaOS's /DATA/AppData/plex/config is the Service volume "config", kept in a Storage Space
- plex: CasaOS's shared /DATA/Media is the shared volume "media"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails
- PGID, which CasaOS sets itself, defaults to "1000"
- PUID, which CasaOS sets itself, defaults to "1000"

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The Node's own network is an optional feature (discovery), as Plex documents it for finding and claiming the server; without it the Service is on its own network and Plex is claimed with a token.
- The graphics card is a device setting the person picks, an optional feature (hardware_transcoding), instead of the whole of /dev/dri.
- /dev/dvb (TV tuners) is dropped: Maître does not support other devices yet.
- TZ is a setting, the Node's time zone; health is /identity.
- No project: Plex Media Server is not developed in public, so the entry has no stars.
