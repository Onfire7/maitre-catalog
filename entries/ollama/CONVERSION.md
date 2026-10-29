# Conversion of Ollama - CPU

From `ollama-cpu`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- ollama asks for AddDevice=/dev/dri:/dev/dri:rwm, which a Trusted Device must allow at install; keep it only if the app needs it, and declare it under grants: with why (optional: if the app works without it)
- ollama asks for AddDevice=/dev/kfd:/dev/kfd:rwm, which Maître does not support yet (it needs SELinux letting a container use the device (container-selinux's container_use_devices boolean, off on Fedora, or a narrower rule) set in the Node image, checked on a Node with the device plugged in); find another way, or leave the entry out

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-ollama-cpu: container_name "big-bear-ollama-cpu" is dropped; Maître names the container, and other containers reach it as "big-bear-ollama-cpu"
- big-bear-ollama-cpu: CasaOS's /DATA/AppData/ollama/.ollama is the Service volume "ollama", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The AMD GPU devices (/dev/kfd, /dev/dri) are dropped: /dev/kfd is not supported yet, and /dev/dri alone does not run ROCm. It runs on the processor, as Big Bear's CPU variant is meant to.
- Health is / ("Ollama is running").
