```text
    __ __               __     _      __      __          __  
   / //_/__  ____  ____/ /____(_)____/ /__   / /   ____ _/ /_ 
  / ,< / _ \/ __ \/ __  / ___/ / ___/ //_/  / /   / __ `/ __ \
 / /| /  __/ / / / /_/ / /  / / /__/ ,<    / /___/ /_/ / /_/ /
/_/ |_\___/_/ /_/\__,_/_/  /_/\___/_/|_|  /_____/\__,_/_.___/ 
                                                              
```
================================================================================
WELCOME TO THE LAB. 
Where containers live, services thrive, and uptime is (mostly) guaranteed.
================================================================================

This repository houses the Docker Compose configurations for the Kendrick Homelab.
Everything needed to spin up the core infrastructure, management tools, and
entertainment services is right here.

```text
  ___        __               _                   _                  
 |_ _|_ __  / _|_ __ __ _ ___| |_ _ __ _   _  ___| |_ _   _ _ __ ___ 
  | || '_ \| |_| '__/ _` / __| __| '__| | | |/ __| __| | | | '__/ _ \
  | || | | |  _| | | (_| \__ \ |_| |  | |_| | (__| |_| |_| | | |  __/
 |___|_| |_|_| |_|  \__,_|___/\__|_|   \__,_|\___|\__|\__,_|_|  \___|
                                                                     
```
The backbone of the operation. Without these, nothing talks to anything.

*   **DNS / AdBlocker**: `dns/adguard` - AdGuard Home for network-wide ad blocking and DNS management.
*   **Reverse Proxy**: `proxies/npm` - Nginx Proxy Manager to handle SSL and route traffic.
*   **Remote Access**: `remote_access/cloudflared` - Cloudflare Tunnel for secure remote access.

```text
  __  __                                                   _   
 |  \/  | __ _ _ __   __ _  __ _  ___ _ __ ___   ___ _ __ | |_ 
 | |\/| |/ _` | '_ \ / _` |/ _` |/ _ \ '_ ` _ \ / _ \ '_ \| __|
 | |  | | (_| | | | | (_| | (_| |  __/ | | | | |  __/ | | | |_ 
 |_|  |_|\__,_|_| |_|\__,_|\__, |\___|_| |_| |_|\___|_| |_|\__|
                           |___/                               
```
Tools to keep the ship sailing smooth.

*   **Access Management**: `access_management/authentik` - Identity provider and SSO service (Authentik).
*   **Container Management**: `container_management/portainer` - Visual management for Docker.
*   **Version Control**: `version_control/gittea` - Self-hosted Git service (Gitea).

```text
  _____       _            _        _                            _   
 | ____|_ __ | |_ ___ _ __| |_ __ _(_)_ __  _ __ ___   ___ _ __ | |_ 
 |  _| | '_ \| __/ _ \ '__| __/ _` | | '_ \| '_ ` _ \ / _ \ '_ \| __|
 | |___| | | | ||  __/ |  | || (_| | | | | | | | | | |  __/ | | | |_ 
 |_____|_| |_|\__\___|_|   \__\__,_|_|_| |_|_| |_| |_|\___|_| |_|\__|
                                                                     
```
Because all work and no play makes the server a dull boy.

*   **Books**: `books/booklore` - eBook management (Booklore).
*   **Games**: `games/core-keeper` - Dedicated server for Core Keeper.
*   **Media - Jellyfin**: `media/jellyfin` - Jellyfin Media Server.
*   **Media - Plex**: `media/plex` - Plex Media Server.
*   **Media - ArrStack**: `media/arrstack` - The *Arr stack.

### Directory Structure

```
.
├── books/
│   └── booklore/
├── container_management/
│   └── portainer/
├── dns/
│   └── adguard/
├── games/
│   └── core-keeper/
├── media/
├── proxies/
│   └── npm/
├── remote_access/
│   └── cloudflared/
├── version_control/
│   └── gittea/
└── volumes/
```

--------------------------------------------------------------------------------
Generated with <3 and figlet.
