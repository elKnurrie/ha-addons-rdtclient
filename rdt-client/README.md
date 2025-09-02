# RDT Client (Home Assistant Add-on)

This add-on runs the official https://hub.docker.com/r/rogerfar/rdtclient container.

## Configuration

No YAML options. After installing and starting:

1. Open the **Web UI** (port 6500).
2. In **Settings**:
   - **Download path**: `/share/rdt-downloads` (create if missing).
   - **Database path**: keep default `/data/db/rdtclient.db`.

> `/share` is mapped from the Home Assistant host, making downloaded files
> accessible to other add-ons and via Samba/NFS add-ons if you use them.

## Ports

- **6500/tcp** – Web UI

## Data Locations (inside the container)

- **`/data/db`** – SQLite database (`rdtclient.db`)
- **`/share/rdt-downloads`** – recommended download directory

## Update Policy

The add-on tracks the upstream Docker image tag `latest`. Update the add-on from
the Add-on Store to pull newer images.

## Troubleshooting

- If the UI doesn’t load, ensure port `6500` isn’t used by another add-on.
- Verify the **Download path** exists and is writable (`/share/rdt-downloads`).
- For ARM devices, ensure you’re on a supported architecture (amd64/aarch64/armv7).

## Links

- Upstream project: https://github.com/rogerfar/rdt-client  
- Docker image tags: https://hub.docker.com/r/rogerfar/rdtclient/tags
