FROM rogerfar/rdtclient:latest

# Install jq to read /data/options.json written by Home Assistant
RUN apk add --no-cache jq

# Add s6-rc cont-init script
COPY rootfs/ /

# Ensure proper permissions for all S6 overlay components and specifically s6-overlay-suexec
RUN find /etc/cont-init.d -type f -exec chmod +x {} \; 2>/dev/null || true && \
    find /etc/services.d -type f -name "run" -exec chmod +x {} \; 2>/dev/null || true && \
    find /etc/services.d -type f -name "finish" -exec chmod +x {} \; 2>/dev/null || true && \
    chmod +x /init 2>/dev/null || true && \
    find /package -type f -executable -exec chmod +x {} \; 2>/dev/null || true && \
    find /run/s6 -type f -exec chmod +x {} \; 2>/dev/null || true && \
    chmod +x /docker-mods 2>/dev/null || true && \
    find /command -type f -exec chmod +x {} \; 2>/dev/null || true && \
    find /usr/bin -name "*s6*" -exec chmod +x {} \; 2>/dev/null || true && \
    find /bin -name "*s6*" -exec chmod +x {} \; 2>/dev/null || true && \
    chmod +x /usr/bin/s6-overlay-suexec 2>/dev/null || true && \
    chmod +x /bin/s6-overlay-suexec 2>/dev/null || true
