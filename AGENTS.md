# Repository Architecture & Deployment Guide

This document outlines the structure and deployment strategy for the Kendrick Homelab repository. It is intended to guide AI agents and developers in understanding the system's organization.

## 1. Overview

This repository serves as the "Infrastructure as Code" (IaC) source for a self-hosted homelab. It is designed to be consumed by **Portainer** using its Git integration feature (Stacks).

-   **Primary Goal:** specific, modular deployment of Docker services.
-   **Deployment Method:** Portainer Stacks (Git Repository).
-   **Orchestration:** Docker Compose.

## 2. Directory Structure

The repository follows a strict **Category > Service > Configuration** hierarchy. This ensures that every service is self-contained and easily locatable.

```text
/
├── category_name/           # e.g., "access_management", "media"
│   └── service_name/        # e.g., "authentik", "jellyfin"
│       ├── docker-compose.yml  # The service definition
│       └── .env.example        # (Optional) Template for environment variables
├── backups/                 # Backup configurations
├── dashboards/              # Dashboard services (e.g., Homepage)
└── monitoring/              # System monitoring stack
```

### Naming Conventions
-   **Categories:** Lowercase, snake_case (e.g., `access_management`).
-   **Services:** Lowercase, hyphen-separated if needed (e.g., `core-keeper`).
-   **Files:** Strictly `docker-compose.yml` for Portainer compatibility.

## 3. Deployment Strategy (Portainer)

Each subdirectory containing a `docker-compose.yml` is intended to be deployed as a separate **Stack** in Portainer.

-   **Repository URL:** This git repository.
-   **Compose Path:** Relative path to the file (e.g., `proxies/traefik/docker-compose.yml`).
-   **Environment Variables:** injected via the Portainer UI ("Environment variables" section) for each stack. Do not hardcode secrets in Git.
-   **Security:** Never include actual secrets (API keys, passwords) in `docker-compose.yml`. Use environment variable placeholders (e.g., `${API_KEY}`).

## 4. Common Patterns & Configuration

### Networking
-   **External Network:** Most public-facing services connect to a pre-defined external network (typically `traefik_public` or similar) to allow the reverse proxy to route traffic to them.
-   **Internal Communication:** Services within the same stack communicate via the default bridge network created by Docker Compose.

### Reverse Proxy (Traefik/NPM)
-   **Traefik:** Used as the primary ingress controller. Services use labels (e.g., `traefik.enable=true`) to expose themselves.
-   **Nginx Proxy Manager (NPM):** Available as an alternative or secondary proxy in `proxies/npm`.

### Dashboard Integration (Homepage)
-   **Discovery:** Services utilize specific Docker labels (e.g., `homepage.group`, `homepage.name`) to automatically register themselves on the central dashboard.

### Environment Variables
Common variables expected across stacks:
-   `DOMAIN`: The root domain name (e.g., `example.com`).
-   `CONFIG_ROOT`: Path on the host system where persistent configuration is stored.
-   `PUID`/`PGID`: User and Group IDs for file permission management.

## 5. Service Inventory

| Category             | Services Included |
|----------------------|-------------------|
| **Access Management**| Authentik |
| **Backups**          | Zerobyte |
| **Container Mgmt**   | Portainer |
| **Dashboards**       | Homepage |
| **DNS**              | AdGuard Home, DuckDNS |
| **Games**            | Core Keeper |
| **Media**            | ArrStack (Radarr/Sonarr etc.), Jellyfin, Plex |
| **Monitoring**       | Beszel, Glances, Uptime Kuma |
| **Proxies**          | Nginx Proxy Manager (NPM), Traefik |
| **Remote Access**    | Cloudflared |
| **Version Control**  | Gitea |
