# Media Server Docker Setup

This Docker setup provides a comprehensive media server solution, comprising various essential services for managing and accessing your media collection. The setup includes Plex, Radarr, Sonarr, Bazarr, Prowlarr, and qBittorrent, all running as Docker containers.

## Services Included

### Plex
- **Image**: lscr.io/linuxserver/plex:latest
- **Container Name**: plex
- **Description**: Plex is a media server allowing you to organize, stream, and access your media content.
- **Ports**: No ports explicitly exposed, uses host network mode.

### Radarr
- **Image**: lscr.io/linuxserver/radarr:latest
- **Container Name**: radarr
- **Description**: Radarr is a movie management tool that automatically grabs your movies from various sources.
- **Ports**: Exposes port 7878 for web UI.

### Sonarr
- **Image**: lscr.io/linuxserver/sonarr:latest
- **Container Name**: sonarr
- **Description**: Sonarr is a TV series management tool for automatically downloading TV shows.
- **Ports**: Exposes port 8989 for web UI.

### Bazarr
- **Image**: lscr.io/linuxserver/bazarr:latest
- **Container Name**: bazarr
- **Description**: Bazarr is a subtitle downloader and manager for TV series.
- **Ports**: Exposes port 6767 for web UI.

### Prowlarr
- **Image**: lscr.io/linuxserver/prowlarr:latest
- **Container Name**: prowlarr
- **Description**: Prowlarr is a tool for indexing and managing your Usenet and torrent collections.
- **Ports**: Exposes port 9696 for web UI.

### qBittorrent
- **Image**: lscr.io/linuxserver/qbittorrent:latest
- **Container Name**: qbittorrent
- **Description**: qBittorrent is a BitTorrent client application, used for downloading and managing torrents.
- **Ports**: Exposes port 8080 for web UI, and port 6881 for torrenting.

## Prerequisites
- Docker installed on your system.
- Configuration of environment variables:
  - `PUID`: User ID for file permissions within containers.
  - `PGID`: Group ID for file permissions within containers.
  - `TZ`: Your timezone.

## Setup Instructions
1. Clone this repository or create a `docker-compose.yml` file with the provided configuration.
2. Set up the necessary environment variables in your system or modify them directly in the `docker-compose.yml` file.
3. Replace `${MEDIA_SERVER_APPS_DIR}` and `${MEDIA_SERVER_DATA_DIR}` with your preferred directories for application configurations and media storage, respectively.
4. Run `docker-compose up -d` in the directory containing your `docker-compose.yml` file to start all the services as Docker containers in detached mode.

## Accessing Services
- Once the containers are running, you can access the web interfaces of each service using the following URLs:
  - **Plex**: [http://localhost:32400/web](http://localhost:32400/web)
  - **Radarr**: [http://localhost:7878](http://localhost:7878)
  - **Sonarr**: [http://localhost:8989](http://localhost:8989)
  - **Bazarr**: [http://localhost:6767](http://localhost:6767)
  - **Prowlarr**: [http://localhost:9696](http://localhost:9696)
  - **qBittorrent**: [http://localhost:8080](http://localhost:8080)
- Remember that you need to manually configure the services between them so that they can work together.
  - You will need to connect Sonarr/Radarr to Prowlarr so that it can push configurations.
  - Add trackers to Prowlarr.
  - Connect Sonarr/Radarr to Bazarr.
  - Add sources to Bazarr so that it can search for subtitles.

## Notes
- Make sure to keep your media files organized and accessible to the respective services as configured in the volumes section.
- Adjust port mappings and configurations as needed, ensuring they don't conflict with existing services on your system.
- This docker compose was built following the recomendations of this guide: https://trash-guides.info/
