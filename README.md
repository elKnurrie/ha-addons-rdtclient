# RDT Client – Home Assistant Add-on

**Current Version: 0.2.7**

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

### Version 0.2.7
- **Maximum permissive AppArmor profile**: Added complain flag and maximum permissions to resolve s6-overlay-suexec issues
- **Fixed S6 overlay suexec permissions**: Specific permission fixes for s6-overlay-suexec binary in multiple locations
- **Enhanced debugging capabilities**: Complain mode allows full functionality while providing permission debugging
- **Comprehensive S6 binary support**: Complete permission coverage for all S6 overlay components

### Version 0.2.6
- **Simplified AppArmor to highly permissive profile**: Resolved all S6 overlay permission issues with comprehensive file access
- **Enhanced file permission management**: Recursive permission setting for all S6 overlay components including docker-mods
- **Fixed S6 supervision errors**: Resolved s6-supervise, s6rc-oneshot-runner, and rc.init permission denied errors
- **Improved container initialization**: Comprehensive permission fixes for all S6 overlay scripts and services

### Version 0.2.5
- **Fixed S6 overlay init system**: Resolved persistent permission denied errors for S6 basedir/bin/init
- **Comprehensive AppArmor permissions**: Added full support for S6 overlay file system structure
- **Enhanced container capabilities**: Added sys_admin and improved file system access permissions
- **Better init system support**: Explicit permissions for all S6 overlay components and runtime directories

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
