# Conversion of Gitea

From `docker-compose.yml`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- gitea: deploy.resources reservations (MemoryLow=) are dropped; Maître sets no reservations
- gitea: container_name "gitea" is dropped; Maître names the container, and other containers reach it as "gitea"
- gitea: CasaOS's /DATA/AppData/gitea/data is the Service volume "data", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- No project: for the entry's popularity; add the app's repository on GitHub, Codeberg or GitLab

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- project: https://github.com/go-gitea/gitea, Gitea's own repository.
- GITEA__server__ROOT_URL is the Service's address on the home network, http://<name>.local/, and SSH_DOMAIN and SSH_PORT say that clones over SSH go to <name>.local on the Node's port 222 (the file published 222 without telling Gitea), so the addresses Gitea shows for a repository work; its setup page offers both to change.
- Health is /api/healthz.
