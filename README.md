# RDT Client – Home Assistant Add-on

This repository provides a Home Assistant add-on wrapping the official
https://hub.docker.com/r/rogerfar/rdtclient image.

- Web UI: http://`<homeassistant>`:6500
- Default DB path: `/data/db`
- **Download path** is configurable from the add-on UI and applied **automatically** on start

## Add to Home Assistant

1. Open **Settings → Add-ons → Add-on Store**.
2. Click **⋮ (top-right) → Repositories** and add:  
   `https://github.com/elKnurrie/ha-addons-rdtclient`
3. Find **RDT Client** under the store, **Install**, then **Start**.

After first start, the add-on automatically links rdt-client's internal `/data/downloads`
to the path you choose in the **Configuration** tab (default `/share/rdt-downloads`).
