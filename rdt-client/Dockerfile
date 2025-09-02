FROM rogerfar/rdtclient:latest

# Install jq to read /data/options.json written by Home Assistant
RUN apt-get update     && apt-get install -y --no-install-recommends jq     && rm -rf /var/lib/apt/lists/*

# Add s6-rc cont-init script
COPY rootfs/ /
