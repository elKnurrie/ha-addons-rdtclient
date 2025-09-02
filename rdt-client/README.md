# RDT Client (Home Assistant Add-on)

**Version 0.2.7**

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

## Recent Updates (v0.2.7)
- **Maximum permissive AppArmor profile**: Added complain flag and full permissions (rwklmx) to resolve all permission issues
- **Fixed s6-overlay-suexec permissions**: Specific permission fixes for the S6 overlay suexec binary
- **Enhanced S6 binary permissions**: Added comprehensive permission setting for all S6-related binaries
- **Debug-friendly configuration**: Complain mode allows debugging while maintaining functionality

### Previous Updates (v0.2.6)
- **Simplified AppArmor profile**: Switched to highly permissive profile to resolve all S6 overlay permission issues
- **Comprehensive file permissions**: Added recursive permission setting for all S6 overlay components
- **Fixed docker-mods and rc.init errors**: Enhanced permissions for all S6 initialization scripts
- **Improved container compatibility**: Very permissive profile while maintaining essential security boundaries

### Previous Updates (v0.2.5)
- **Fixed S6 overlay permissions**: Resolved persistent "/init: Permission denied" and S6 basedir/bin/init errors
- **Enhanced AppArmor S6 support**: Added comprehensive permissions for S6 overlay init system
- **Improved system capabilities**: Added sys_admin capability for container operations
- **Better file system access**: Enhanced permissions for /proc, /sys, /opt, and /home directories

### Previous Updates (v0.2.4)
- **Fixed init script permissions**: Resolved "/init: Permission denied" error during container startup
- **Enhanced AppArmor capabilities**: Added necessary permissions for chown, setuid, setgid operations
- **Improved container initialization**: Added explicit permission setting for init scripts

### Previous Updates (v0.2.3)
- **Fixed AppArmor profile issues**: Resolved installation errors related to security profile loading
- **Enhanced security permissions**: Updated AppArmor configuration for better Home Assistant compatibility
- **Improved network and file system access**: Added support for IPv6 and additional system paths

### Previous Updates (v0.2.2)
- Fixed Docker build issues by updating package manager commands for Alpine Linux compatibility
- Improved error handling and setup process
