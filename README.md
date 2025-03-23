# NetGenie Docker Compose Setup ✨

Welcome to **NetGenie**, your all-in-one networking and privacy stack! 🌐 This Docker Compose setup includes essential services to enhance your network privacy, block ads, and securely route your traffic. Services include **Pi-hole** for ad-blocking, **WireGuard** for VPN, and powerful monitoring with **Prometheus** and **Grafana**. Plus, you get easy container management with **Portainer**!

## 📌 Table of Contents
- [⚡ Prerequisites](#-prerequisites)
- [🛠️ Services Overview](#-services-overview)
- [⚙️ Configuration](#-configuration)
- [▶️ Usage](#-usage)
- [🌍 Ports](#-ports)
- [💾 Volumes](#-volumes)
- [🔧 Environment Variables](#-environment-variables)
- [📜 License](#-license)

## ⚡ Prerequisites
Before you begin, ensure you have the following installed:

- [🐳 Docker](https://docs.docker.com/get-docker/)
- [📦 Docker Compose](https://docs.docker.com/compose/install/)

## 🛠️ Services Overview

### 🔹 1. Pi-hole (DNS & Ad-blocking)
- **Image:** `pihole/pihole`
- **Purpose:** A DNS server that blocks ads across your entire network.
- **Configuration:**
  - Web UI accessible on port **8080**.
  - Default password: `your_admin_password`.

### 🔹 2. WireGuard (Secure VPN)
- **Image:** `wg-easy/wg-easy`
- **Purpose:** A VPN solution for routing network traffic securely through a private server.
- **Configuration:**
  - Web UI accessible at port **51821**.
  - Password: `your_secure_password`.

### 🔹 3. Prometheus (Monitoring)
- **Image:** `prom/prometheus`
- **Purpose:** Collects network metrics like traffic and DNS requests.
- **Configuration:**
  - Web UI accessible on port **9090**.

### 🔹 4. Grafana (Visualization)
- **Image:** `grafana/grafana`
- **Purpose:** Visualizes metrics collected by Prometheus for network insights.
- **Configuration:**
  - Web UI accessible on port **3000**.
  - Default password: `admin_password`.

### 🔹 5. Portainer (Docker Management)
- **Image:** `portainer/portainer-ce`
- **Purpose:** A web-based UI for managing Docker containers.
- **Configuration:**
  - Web UI accessible on port **9000**.

### 🔹 6. Nginx (Optional Reverse Proxy)
- **Image:** `nginx:latest`
- **Purpose:** A reverse proxy for routing traffic securely between containers or exposing web services.
- **Configuration:**
  - Web UI accessible on ports **80** and **443**.

## ⚙️ Configuration

### 1. Pi-hole Setup
Edit the **environment** section under the Pi-hole service to include your **admin password**:
```yaml
environment:
  - PIHOLE_PASSWORD=your_admin_password
2. WireGuard Setup
Edit the environment section under the WireGuard service to configure the VPN host and password:

yaml
Copy
Edit
environment:
  - WG_HOST=your-server-ip
  - PASSWORD=your_secure_password
3. Volume Paths
Ensure the volume paths in the volumes section match your local directory structure. For example:

yaml
Copy
Edit
volumes:
  - /home/your-user/docker/netnectar/pihole/etc-pihole:/etc/pihole
  - /home/your-user/docker/netnectar/pihole/etc-dnsmasq.d:/etc/dnsmasq.d
▶️ Usage
Clone this repository or copy the docker-compose.yml file to your server.

Update the configuration as described above.

Start the stack using Docker Compose:

bash
Copy
Edit
docker-compose up -d
Access services via their respective ports (see Ports).

🌍 Ports
Service	Port	Purpose
Pi-hole	8080	Web UI for Pi-hole
WireGuard	51821	Web UI for WireGuard
Prometheus	9090	Web UI for Prometheus
Grafana	3000	Web UI for Grafana
Portainer	9000	Web UI for Portainer
Nginx	80/443	Web UI for Nginx (optional)
💾 Volumes
Ensure the following directories exist on your host machine:

swift
Copy
Edit
/home/your-user/docker/netnectar/pihole
/home/your-user/docker/netnectar/wg-easy
/home/your-user/docker/netnectar/prometheus
/home/your-user/docker/netnectar/grafana
/home/your-user/docker/netnectar/portainer
/home/your-user/docker/netnectar/nginx
🔧 Environment Variables
Key environment variables for configuration:

PIHOLE_PASSWORD: Admin password for Pi-hole's web UI.

WG_HOST: IP address of your WireGuard server.

PASSWORD: Web UI password for WireGuard.

GF_SECURITY_ADMIN_PASSWORD: Admin password for Grafana.

TZ: Timezone for containers.

📜 License
This project is open-source and available under the MIT License. Feel free to modify and distribute it as needed! 📝✨

yaml
Copy
Edit

---

### Key Features:
- **NetGenie** provides an all-in-one solution for network privacy, ad-blocking, secure VPN, and monitoring.
- Easily deployable via Docker Compose with fully customizable environment variables and ports.

Let me know if you need further adjustments or additions to the README!





You said:
in license note i own no projects, its just a simple stack
ChatGPT said:
Here’s your updated README.md:

markdown
Copy
Edit
# 🚀 NetGenie - Networking Stack with Pi-hole and WireGuard

Welcome to **NetGenie**! 🌐 This simple Docker Compose stack brings together powerful networking tools like **Pi-hole**, **WireGuard**, and **Portainer** to enhance privacy, security, and network monitoring for your home or small office setup. 🛡️

NetGenie helps you block ads across your network, route traffic securely with a VPN, and manage Docker containers with ease. Below is a detailed breakdown of the services included in this stack.

## 📌 Table of Contents
- [⚡ Prerequisites](#-prerequisites)
- [🛠️ Services Overview](#-services-overview)
- [⚙️ Configuration](#-configuration)
- [▶️ Usage](#-usage)
- [🌍 Ports](#-ports)
- [💾 Volumes](#-volumes)
- [🔧 Environment Variables](#-environment-variables)
- [📜 License](#-license)

## ⚡ Prerequisites
Before you begin, ensure you have the following installed:

- [🐳 Docker](https://docs.docker.com/get-docker/)
- [📦 Docker Compose](https://docs.docker.com/compose/install/)
- A **WireGuard** VPN configuration (with valid credentials) for the WireGuard service.

## 🛠️ Services Overview

### 🔹 1. Pi-hole (Ad Blocker)
- **Image:** `pihole/pihole:latest`
- **Purpose:** Blocks ads across your entire network by acting as a DNS server.
- **Configuration:** 
  - Set up Pi-hole as the DNS resolver for your router or devices to block ads network-wide.
  - Web UI is accessible at port **80** (configurable).

### 🔹 2. WireGuard (VPN)
- **Image:** `wg-easy/wg-easy:latest`
- **Purpose:** Secure VPN service that routes your network traffic through a private server.
- **Configuration:** 
  - WireGuard provides encrypted and private internet browsing.
  - All network traffic is routed through this VPN for enhanced privacy.

### 🔹 3. Portainer (Container Management)
- **Image:** `portainer/portainer-ce:latest`
- **Purpose:** Web UI to manage Docker containers. Easily start, stop, and configure services.

## ⚙️ Configuration

### 🛡️ 1. Pi-hole Setup
- Edit the environment section under the **Pi-hole** service to configure your DNS settings.

### 📂 2. WireGuard Setup
- Edit the **WireGuard** service to configure your VPN credentials and server settings.

### 🔧 3. Portainer Setup
- The **Portainer** service will allow you to manage Docker containers through a web UI.

## ▶️ Usage

1. **Clone this repository** or copy the `docker-compose.yml` file to your server.
2. **Update the configuration** as described above.
3. **Start the stack** using Docker Compose:
   ```bash
   docker-compose up -d
Access services via their respective ports (see Ports).

🌍 Ports
Service	Port	Purpose
Pi-hole	80	🌐 Web UI for Pi-hole (Ad Blocking)
WireGuard	51820	🔒 WireGuard VPN
Portainer	9000	🛠️ Web UI for Portainer (Container Management)
💾 Volumes
Ensure the following directories exist on your host machine for persistent storage:

swift
Copy
Edit
/home/ubuntu/docker/netgenie/pihole
/home/ubuntu/docker/netgenie/wireguard
/home/ubuntu/docker/netgenie/portainer
🔧 Environment Variables
Key environment variables for services:

Pi-hole: DNS1, DNS2, etc. for upstream DNS servers.

WireGuard: WG_PRIVATE_KEY, WG_SERVER_PUBLIC_KEY, etc. for VPN configuration.

📜 License
This project is simply a Docker Compose stack with no ownership of any individual projects. It is open-source and available for free use. You can modify and distribute it as needed. 😊
