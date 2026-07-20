# Homelab Portfolio

This repository documents the design, setup, and ongoing development of my personal homelab.

The purpose of this lab is to build practical experience with Linux administration, networking, Docker, monitoring, remote accesss, automation, and cybersecurity tools.

## Current Environment

### Ubuntu Server VM
- Ubuntu Server
- Docker Engine
- Docker Compose
- OpenSSH Server
- Tailscale

### Docker Services
- Portainer
- Homepage
- Uptime Kuma

### Administration Devices
- Ubuntu cybersecurity laptop
- Windows gaming PC
- Secure remote access through Tailscale
- SSH key authentication

## Current Capabilities

- Remotely administer the Ubuntu Server VM over Tailscale
- Connect through SSH without exposing port 22 to the public internet
- Authenticate using SSH keys
- Manage Docker containers through the command line and Portainer
- Monitor services with Uptime Kuma
- View homelab services through Homepage
- Track documentation and configuration changes with Github

## Repository Structure

```text
.
├── docker
├── docs
│   ├── docker-services.md
│   ├── server-setup.md
│   ├── tailscale-and-ssh.md
│   └── troubleshooting.md
├── images
├── README.md
└── scripts
    └── README.md

