# RDT Client – Home Assistant Add-on

**Current Version: 0.2.4**

This repository provides a Home Assistant add-on wrapping the official
https://hub.docker.com/r/rogerfar/rdtclient image.

**Key Features:**
- Real-Debrid torrent client integration with Home Assistant
- Automatic download path configuration
- Web-based management interface
- Multi-architecture support (amd64, aarch64, armv7)

## Quick Access
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

## Recent Updates

### Version 0.2.4
- **Fixed container startup issues**: Resolved "/init: Permission denied" errors
- **Enhanced execution permissions**: Updated AppArmor profile with proper init system support
- **Improved security capabilities**: Added necessary permissions for user/group management
- **Better container initialization**: Explicit permission setting for all init scripts

### Version 0.2.3
- **Fixed AppArmor profile loading errors**: Resolved installation issues in Home Assistant
- **Enhanced security configuration**: Updated AppArmor permissions for better compatibility
- **Improved system integration**: Added support for IPv6 networking and additional file system access

### Version 0.2.2
- **Fixed Docker build issues**: Resolved compatibility problems with Alpine Linux base image
- **Improved package management**: Updated from apt-get to apk for better reliability
- **Enhanced error handling**: Better setup process and troubleshooting

## Support

If you encounter any issues:
1. Check the add-on logs in Home Assistant
2. Ensure your download path is under `/share` and writable
3. Try restarting the add-on
4. Report issues on [GitHub](https://github.com/elKnurrie/ha-addons-rdtclient/issues)
