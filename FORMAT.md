# Manifest format

`manifest.yaml`, one per entry:

```yaml
id: jellyfin                 # [a-z0-9-], unique, also the Service's default name
name: Jellyfin
summary: one line shown in lists
description: |
  longer text shown on the entry page
icon: icon.svg               # a file beside the manifest, copied from an icon pack
category: media              # media | home | network | tools | infrastructure
image: docker.io/jellyfin/jellyfin:10.10.7@sha256:...   # tag for humans, digest for machines
version: "10.10.7"
project: https://github.com/jellyfin/jellyfin   # the app's own repository (GitHub, Codeberg
                             # or GitLab); its stars are the entry's popularity
exposure: remote             # default exposure level: private | remote
own_login: false             # true if the app has its own accounts (changes Console wording)
infrastructure: false        # DHCP/DNS style: reserved address, early start
host_ports:                  # ports the app must own on the Node itself
  - 53/udp
port_forward: false          # true: the app is meant to be reached from the internet at
                             # host_ports (a game server); the Console offers to have the
                             # router forward them (UPnP). Off until the user turns it on.
web:                         # the page the Console opens; omit for headless apps
  port: 8096
  path: /
volumes:                     # named data dirs; placed at <pool>/<service>/<name>
  - name: config
    path: /config
  - name: media
    path: /media
    size: large              # small | medium | large: hint for Tier choice
    shared: true             # suggest a folder the user picks, shared with other Services (decision 175)
settings:                    # asked at install, available to the template as {{ .Settings.KEY }}
  - key: TZ
    label: Time zone
    type: timezone           # text | number | password | timezone | bool | device
    default: auto
  - key: DB_PASSWORD
    label: Database password
    type: password
    default: generate        # made up at install: 32 letters and digits
health:
  http: /health              # or `cmd: ...`
source:                      # only for an entry converted or imported from elsewhere
  from: compose              # compose | casaos | hand
  url: https://...           # the file it came from
  licence: Apache-2.0        # of that file
  converted: 2026-10-28
```

Volume names are also template fields (`{{ .Volumes.name }}`), so they hold
lowercase letters, digits and underscores, no dashes.

## Several containers

An entry may run several containers, as a Compose file does. It then has no
`image:` or `<id>.container` of its own; it lists `components`, each with a
`<name>.container` template beside the manifest:

```yaml
components:
  - name: server             # [a-z0-9-]; also its host name on the Service's network
    image: ghcr.io/immich-app/immich-server:v3.3.5@sha256:...
    after: [redis, database] # started after these (Compose's depends_on)
  - name: database
    image: ghcr.io/immich-app/postgres:14-...@sha256:...
    wait_healthy: true       # those after it wait for its health check
                             # (depends_on: condition: service_healthy)
  - name: machine-learning
    image: ...
    egress: true             # keeps a route out when the network is internal
network: internal            # optional: the Service's network has no route out
web:
  component: server          # which container serves the page; required
  port: 2283
```

Every container joins the Service's own network under its name, so
`database:5432` reaches the database as in Compose; only the web component is
reachable from other Services, under the Service's name. The agent writes the
ordering, health waits, networks and a `<service>.target` that starts and
stops them together; templates give only their `[Container]` keys.

A bundle may also hold `<name>.volume` and `<name>.network` Quadlet units, for
a Compose file's named volumes. The agent writes them as
`<service>-<name>.volume`, and a container's `Volume=`, `Mount=` and
`Network=` references to them follow. Every `.container` file must be a
component's template.

## Icons

An entry's icon is copied into its folder, never linked, so the Console
needs no other server to show it:

```
maitre catalog icon entries/<id> [name in the packs]
```

copies `icon.svg` (or `icon.png`) from homarr-labs/dashboard-icons
(Apache-2.0), or else selfh.st/icons (CC BY 4.0), at the commit each pack is
at, and records it:

```yaml
icon: icon.svg
source:
  icon:
    pack: dashboard-icons
    licence: Apache-2.0
    url: https://raw.githubusercontent.com/homarr-labs/dashboard-icons/<commit>/svg/<name>.svg
```

`maitre catalog add` does the same for the entry it writes. `catalog-index`
puts the icon in the index as a data URI; `catalog-notice` lists it in
`NOTICE`, which `make gen` keeps current.

## Converting a Compose file

```
maitre catalog add [--id id] [--url url] [--licence spdx] <catalog folder> <compose file or CasaOS app folder>
```

writes `entries/<id>/` from a Compose file: a template per service, its
images pinned by digest, its `${VAR}`s used in `environment:` as settings
(passwords made up at install), its folders and named volumes as Service
volumes, and `depends_on` as `after:` and `wait_healthy:`. Beside them go the
file as it came (`compose.yaml`) and `CONVERSION.md`, the report: what must
be fixed before anything is written, what a person must decide, and what was
changed. What a person must decide is also listed in the manifest:

```yaml
unfinished:
  - The web page is taken to be server's port 9000, of 2 published ports; confirm web.component and web.port
```

An entry with `unfinished:` is not installed by the Console and fails
`catalog-check`; remove the list once each item is settled.

## Checks

An entry is known to work when CI has:

1. built the index: `maitre catalog-index entries` (images pinned by digest);
2. rendered it as a Node does and run Podman's Quadlet on the units, with no
   grants needed: `maitre catalog-check entries [id...]`, inside the
   `maitre-server` image (`--units` prints what it rendered);
3. installed it in the boot test's VM and seen it healthy, for the entries a
   change touches.

## Templates

`<id>.container` is a Podman Quadlet `[Container]` unit with Go template
fields. The agent supplies `.Image`, `.Name`, `.Volumes` (name → host path),
`.Settings`, `.Network` and `.Env`. Entries should keep the template short
and let the agent add `[Service]`/`[Install]` sections.

## Popularity

The Catalog page sorts by popularity: the stars of each entry's `project`,
the repository the app is developed in (not one that only packages it, such
as linuxserver's `docker-*`). The counts live in `popularity.json` beside
`entries/`, not in the manifests, so a weekly refresh does not change every
entry:

```json
{"checked": "2026-10-29", "stars": {"jellyfin": 58783}}
```

`maitre catalog popularity --write entries` refreshes it, and
`maitre catalog-index` adds each entry's `stars` to the index. Maître
Server's weekly CI job does both. A Catalog without the file still loads;
its entries sort after those with stars. Stars on Codeberg and GitLab are
counted the same way but tend to be lower than on GitHub.

## Grants

Maître keeps some options from containers unless a Trusted Device allows
them (decision 189): the Node's own network, devices, capabilities, folders
of the Node outside its Storage Spaces. An entry that needs one declares
it, with why, and the Console asks before installing:

```yaml
grants:
  - option: Network=host      # as the Node names it; AddDevice=* matches any device
    why: Finds the devices on your home network by listening for their announcements.
    optional: discovery       # a feature the person may leave out; omit for a required grant
    without: Add devices by their address instead.
```

An optional grant's option goes inside `{{ if .Grants.<feature> }}` in the
template, so the Service runs without it:

```
{{ if .Grants.discovery }}Network=host
{{ else }}Network={{ .Network }}
{{ end }}
```

`maitre catalog-check` renders the entry with every feature on and off and
fails it when an option is not declared, an optional one stays with its
feature off, a declared one is not used, or Maître does not support the
option yet; the message says what support it needs. Supported today:
`Network=host` (single-container entries; the page is served on its own port
of the Node, and is open to the home network there), GPUs (`AddDevice` of
`/dev/dri`), `AddCapability`, `Sysctl`, `UserNS`, `NoNewPrivileges=false`,
and folders of the Node other than the Podman socket and `/run/dbus`.

## Device settings

```yaml
settings:
  - key: GPU
    label: Graphics card for transcoding
    type: device
    device: video             # serial | video | any
```

The Console offers the Node's devices of that kind; empty means none. Use
it as `{{ with .Settings.GPU }}AddDevice={{ . }}{{ end }}` and declare
`AddDevice=*`.

## Generated secrets

`default: generate` makes a password at install: 32 letters and digits.
`format: hex` or `format: base64` with `bytes: 32` makes that many random
bytes in hex or base64 instead, for apps that want a key of that shape
(Laravel's `APP_KEY=base64:{{ .Settings.APP_KEY }}`).
