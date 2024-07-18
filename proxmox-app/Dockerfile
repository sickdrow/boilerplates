# Use the official Debian 12 Bookworm image
FROM debian:bookworm

# Install dependencies
RUN apt-get update && apt-get install -y \
    gnupg \
    curl \
    lsb-release \
    apt-transport-https \
    software-properties-common

# Add Proxmox repository
RUN echo "deb http://download.proxmox.com/debian/pve bookworm pve-no-subscription" > /etc/apt/sources.list.d/pve.list

# Add Proxmox public key
RUN curl -fsSL http://download.proxmox.com/debian/pve-enterprise.gpg | apt-key add -

# Install Proxmox VE
RUN apt-get update && apt-get install -y \
    proxmox-ve \
    postfix \
    open-iscsi \
    pve-firmware

# Expose Proxmox ports (adjust as needed)
EXPOSE 8006

# Set entrypoint (optional, for starting services)
# CMD ["pve-cluster", "start"]