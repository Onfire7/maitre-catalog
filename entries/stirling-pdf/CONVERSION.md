# Conversion of Stirling-PDF

From `stirling-pdf`, by `maitre catalog add`.

## Needs a person

The entry is unfinished until these are decided and its `unfinished:` list is removed.

- big-bear-stirling-pdf: SECURITY_INITIALLOGIN_PASSWORD is written into the file; make it a setting (default: generate) unless the app relies on this value

## Changed for you

Done differently from the Compose file; check they suit the app.

- big-bear-stirling-pdf: container_name "big-bear-stirling-pdf" is dropped; Maître names the container, and other containers reach it as "big-bear-stirling-pdf"
- big-bear-stirling-pdf: CasaOS's /DATA/AppData/stirling-pdf/tessdata is the Service volume "tessdata", kept in a Storage Space
- big-bear-stirling-pdf: CasaOS's /DATA/AppData/stirling-pdf/configs is the Service volume "configs", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- The initial login is the user admin with a password made up at install (the setting ADMIN_PASSWORD), not the user and password written into the file.
- SECURITY_ENABLE_LOGIN is SECURITY_ENABLELOGIN, the name Stirling-PDF's documentation gives; DOCKER_ENABLE_SECURITY, which its documentation no longer lists, is dropped.
- Health is /api/v1/info/status.
