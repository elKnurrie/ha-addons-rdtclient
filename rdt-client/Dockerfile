FROM rogerfar/rdtclient:latest

# Install jq to read /data/options.json written by Home Assistant
RUN apk add --no-cache jq

# Add s6-rc cont-init script
COPY rootfs/ /

# Ensure proper permissions for init scripts and S6 overlay
RUN chmod +x /etc/cont-init.d/* 2>/dev/null || true && \
    chmod +x /init 2>/dev/null || true && \
    chmod +x /package/admin/s6-overlay-*/libexec/* 2>/dev/null || true && \
    chmod +x /run/s6/basedir/bin/* 2>/dev/null || true
