# RDT Client (Home Assistant Add-on)

**Version 0.2.3**

This add-on runs the official `rogerfar/rdtclient` container, providing Real-Debrid torrent client functionality within Home Assistant.

## Configuration

Set the **download_path** from the add-on UI (default: `/share/rdt-downloads`).
On container start the add-on will automatically:

- Create the folder if it doesn't exist.
- Symlink rdt-client's internal `/data/downloads` to your chosen folder, so rdt-client
  uses it without further manual steps.

### First-run steps

No manual path changes needed in rdt-client. Just start the add-on and open the Web UI.
Keep the default **Database path** `/data/db/rdtclient.db`.

## Ports
- **6500/tcp** – Web UI

## Data locations (inside the container)
- `/data/db` – SQLite database (`rdtclient.db`)
- `/data/downloads` – symlink pointing to your configured `download_path`

## Troubleshooting
- If the add-on doesn't appear, click **Add-on Store → ⋮ → Reload**.
- Ensure your configured path lives under `/share` and is writable.
- If you encounter build issues, make sure you're using the latest version of the add-on.

## Recent Updates (v0.2.3)
- **Fixed AppArmor profile issues**: Resolved installation errors related to security profile loading
- **Enhanced security permissions**: Updated AppArmor configuration for better Home Assistant compatibility
- **Improved network and file system access**: Added support for IPv6 and additional system paths

### Previous Updates (v0.2.2)
- Fixed Docker build issues by updating package manager commands for Alpine Linux compatibility
- Improved error handling and setup process
