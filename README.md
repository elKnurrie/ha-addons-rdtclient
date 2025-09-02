# RDT Client – Home Assistant Add-on

This repository provides a Home Assistant add-on wrapping the official
https://hub.docker.com/r/rogerfar/rdtclient image.

- Web UI: http://`<homeassistant>`:6500
- Default DB path: `/data/db`
- Recommended downloads path: `/share/rdt-downloads`

## Add to Home Assistant

1. Open **Settings → Add-ons → Add-on Store**.
2. Click **⋮ (top-right) → Repositories** and add:  
   `https://github.com/your-user/ha-addons-rdtclient`
3. Find **RDT Client** under the store, **Install**, then **Start**.

After first start, open the web UI and set:
- **Download path**: `/share/rdt-downloads`
- (Optional) Keep the default **Database path**: `/data/db/rdtclient.db`

> The `/share` folder is mapped into the add-on so your downloads are available
> to other add-ons and on the host. Create `/share/rdt-downloads` if it doesn’t exist.
