FROM rogerfar/rdtclient:latest

# Install jq to read /data/options.json written by Home Assistant
RUN apk add --no-cache jq

# Create a simple startup script that works with the base image
COPY <<EOF /usr/local/bin/ha-setup.sh
#!/bin/bash
set -e

# Read download path from Home Assistant options
OPTIONS_FILE="/data/options.json"
DEFAULT_PATH="/share/rdt-downloads"

DOWNLOAD_PATH="\${DEFAULT_PATH}"
if [ -f "\$OPTIONS_FILE" ]; then
  VAL=\$(jq -r '.download_path // empty' "\$OPTIONS_FILE" 2>/dev/null || echo "")
  if [ -n "\${VAL}" ] && [[ "\${VAL}" == /share/* ]]; then
    DOWNLOAD_PATH="\${VAL}"
  fi
fi

# Create download directory
mkdir -p "\$DOWNLOAD_PATH"
chmod 755 "\$DOWNLOAD_PATH"

echo "HA Setup: Download path configured as \$DOWNLOAD_PATH"
EOF

RUN chmod +x /usr/local/bin/ha-setup.sh

# Create a custom init script that runs our setup then delegates to the original
COPY <<EOF /custom-init
#!/bin/bash
# Run our Home Assistant setup
/usr/local/bin/ha-setup.sh

# Delegate to the original init system
exec /init "\$@"
EOF

RUN chmod +x /custom-init

# Use our custom init
ENTRYPOINT ["/custom-init"]
