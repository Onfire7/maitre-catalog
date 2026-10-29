# Conversion of Eclipse Mosquitto

From `mosquitto`, by `maitre catalog add`.

## Changed for you

Done differently from the Compose file; check they suit the app.

- app: CasaOS's /DATA/AppData/mosquitto/config is the Service volume "config", kept in a Storage Space
- app: CasaOS's /DATA/AppData/mosquitto/data is the Service volume "data", kept in a Storage Space
- app: CasaOS's /DATA/AppData/mosquitto/log is the Service volume "log", kept in a Storage Space
- restart: policies are replaced by Maître's: each container restarts when it fails

## Notes

- project: https://github.com/eclipse-mosquitto/mosquitto, from the image's source label; its stars are the entry's popularity

## Edited by hand

After the conversion, for the Catalog:

- The summary and description are shorter, in the Catalog's words.
- Headless: 1883 is MQTT, not a web page, so the entry has no web: and owns port 1883 of the Node (host_ports) for the devices on the home network. The WebSocket port 9001 is dropped.
- It runs with the configuration the image ships for this, /mosquitto-no-auth.conf (a listener on 1883, no passwords), since Mosquitto 2 without a configuration listens only inside its container.
