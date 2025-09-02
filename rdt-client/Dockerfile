FROM rogerfar/rdtclient:latest

# Install jq to read /data/options.json written by Home Assistant
RUN apk add --no-cache jq

# Add s6-rc cont-init script
COPY rootfs/ /

# Ensure proper permissions for init scripts
RUN chmod +x /etc/cont-init.d/* 2>/dev/null || true
