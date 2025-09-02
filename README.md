# RDT Client – Home Assistant Add-on

**Current Version: 0.3.2**

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

After first start, you'll need to manually configure the download path in RDT Client's settings to match the path you configured in the add-on (default `/share/rdt-downloads`).

## Recent Updates

### Version 0.3.2 - Enhanced S6 Overlay Support
- **Fixed S6 runtime directory creation**: Resolved s6-mkdir permission denied errors for /run/s6 and /run/service
- **Comprehensive S6 overlay permissions**: Added all necessary capabilities and file permissions for S6 system
- **Enhanced runtime support**: Better permissions for /run, /var, /proc, and /sys directories
- **Complete S6 binary coverage**: Permissions for all S6 overlay tools and utilities

### Version 0.3.1 - Fixed Init System Compatibility  
- **Custom init wrapper**: Created `/custom-init` that runs Home Assistant setup then delegates to original `/init`
- **Preserved base image functionality**: Works with the existing S6 overlay system instead of replacing it
- **Enhanced AppArmor permissions**: Added support for both custom scripts and original init system
- **Better compatibility**: Respects the base image's architecture while adding Home Assistant integration

### Version 0.3.0 - Major Simplification
- **Removed S6 overlay dependencies**: Eliminated all S6 overlay permission issues by using a simple startup script
- **Simplified architecture**: Direct execution of RDT Client without complex init systems
- **Cleaner security profile**: Minimal AppArmor configuration focused only on necessary permissions
- **Manual configuration approach**: Users configure download paths directly in RDT Client (more reliable)
- **Better stability**: No more permission denied errors or init system conflicts

### Previous Versions (0.2.x)
- Multiple iterations attempting to fix S6 overlay permission issues
- Enhanced AppArmor profiles and permission management
- Fixed Docker build compatibility with Alpine Linux

## Support

If you encounter any issues:
1. Check the add-on logs in Home Assistant
2. Ensure your download path is under `/share` and writable
3. Try restarting the add-on
4. Report issues on [GitHub](https://github.com/elKnurrie/ha-addons-rdtclient/issues)
