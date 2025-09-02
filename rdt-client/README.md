# RDT Client (Home Assistant Add-on)

This add-on runs the official `rogerfar/rdtclient` container.

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
