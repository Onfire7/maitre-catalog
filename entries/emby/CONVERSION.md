# Conversion of Emby

From `Emby`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- emby asks for AddDevice=/dev/dri:/dev/dri:rwm, which a Trusted Device must allow at install; keep it only if the app needs it, and declare it under grants: with why (optional: if the app works without it)
- emby asks for AddDevice=/dev/vchiq:/dev/vchiq:rwm, which Maître does not support yet (it needs SELinux letting a container use the device (container-selinux's container_use_devices boolean, off on Fedora, or a narrower rule) set in the Node image, checked on a Node with the device plugged in); find another way, or leave the entry out
- emby asks for AddDevice=/dev/video10:/dev/video10:rwm, which Maître does not support yet (it needs SELinux letting a container use the device (container-selinux's container_use_devices boolean, off on Fedora, or a narrower rule) set in the Node image, checked on a Node with the device plugged in); find another way, or leave the entry out
- emby asks for AddDevice=/dev/video11:/dev/video11:rwm, which Maître does not support yet (it needs SELinux letting a container use the device (container-selinux's container_use_devices boolean, off on Fedora, or a narrower rule) set in the Node image, checked on a Node with the device plugged in); find another way, or leave the entry out
- emby asks for AddDevice=/dev/video12:/dev/video12:rwm, which Maître does not support yet (it needs SELinux letting a container use the device (container-selinux's container_use_devices boolean, off on Fedora, or a narrower rule) set in the Node image, checked on a Node with the device plugged in); find another way, or leave the entry out

## Changed for you

Done differently from the Compose file; check they suit the app.

- emby: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- emby: container_name "emby" is dropped; Maître names the container, and other containers reach it as "emby"
- emby: CasaOS's /DATA/AppData/emby/config is the Service volume "config", kept in a Storage Space
- emby: CasaOS's shared /DATA/Media/TV Shows is the shared volume "tv_shows"; the user picks the folder at install
- emby: CasaOS's shared /DATA/Media/Movies is the shared volume "movies"; the user picks the folder at install
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The graphics card is a device setting the person picks, an optional feature (hardware_transcoding), instead of the whole of /dev/dri.
- The Raspberry Pi devices (/dev/vchiq, /dev/video1x) are dropped: Maître does not support other devices yet.
- Its HTTPS port 8920 is dropped: Maître serves the page over its own connection.
- Health is /emby/System/Ping.
