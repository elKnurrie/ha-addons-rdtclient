FROM rogerfar/rdtclient:latest

# Install jq to read /data/options.json written by Home Assistant
RUN apk add --no-cache jq

# Create a simple startup script
COPY <<EOF /usr/local/bin/start.sh
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

# Set environment variable for RDT Client
export RDT_DOWNLOAD_PATH="\$DOWNLOAD_PATH"

echo "RDT Client starting with download path: \$DOWNLOAD_PATH"

# Start the original RDT Client
exec /app/RDTClient
EOF

RUN chmod +x /usr/local/bin/start.sh

# Use our simple startup script
CMD ["/usr/local/bin/start.sh"]
