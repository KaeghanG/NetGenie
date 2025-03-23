# NetGenie Docker Compose Stack

Welcome to **NetGenie**! 🧞‍♂️ This stack sets up a simple, secure, and private networking environment with Pi-hole, WireGuard, and Portainer. It provides ad-blocking across your network, a secure VPN, and an easy-to-use interface to manage your Docker containers. 🚀

## Table of Contents
- [Prerequisites](#prerequisites)
- [Services Overview](#services-overview)
- [Configuration](#configuration)


## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Services Overview

### 1. Pi-hole 🧹
Pi-hole acts as a **DNS server** that blocks ads across your entire network. You can configure your router or devices to use Pi-hole as the DNS resolver, ensuring ad-blocking is applied everywhere.

- **Web UI:** Available on port 80 (configurable).
- **Configuration:** Set your Pi-hole web password and DNS settings in the environment variables.

### 2. WireGuard 🔒
WireGuard is a secure **VPN service** that tunnels your network traffic through a private server, encrypting your browsing and enhancing your privacy.

- **Web UI:** Manage WireGuard VPN settings via the web interface.
- **Configuration:** Set your VPN credentials and host address in the environment variables.

### 3. Portainer ⚙️
Portainer is a **web-based UI** for managing Docker containers. It allows you to view, start, stop, and configure all your Docker services in an easy-to-use interface.

- **Web UI:** Accessible at port 9000.

## Configuration

1. **Pi-hole:**
   - Set your **web password** and **DNS settings** (Cloudflare, Google DNS, or custom).
   - The Pi-hole web UI will be available on port 80.
   
2. **WireGuard:**
   - Configure your **VPN host** and set a **password** for the web UI.
   - WireGuard will be exposed on port 51820.

3. **Portainer:**
   - Portainer will be available at port 9000.
   - You can manage all Docker services via its UI.

### Environment Variables:
- `WEBPASSWORD`: Pi-hole web password.
- `WG_HOST`: Hostname for WireGuard VPN.
- `PASSWORD`: Password for the WireGuard web UI.
