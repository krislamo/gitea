# Gitea Deployment Repository
Gitea is excellent as a Git service within Docker environments, boasting
features like simple installation and setup, being lightweight and supporting
the latest Git features. While similar, the docker-compose files available here
cater to different use cases for deploying Gitea.

## Variables
Here's a brief explanation of the variables used in the docker-compose files:

### Docker Settings
- `IMAGE`: The name of the Docker image (default: `gitea/gitea`).
- `VERSION`: The tag of the Docker image (default: `latest`).
- `NAME`: The name assigned to the created container (default: `gitea`).

### Gitea Database Settings
- `DB_TYPE`: The database type (default: `mysql`).
- `DB_HOST`: The database host (default: `host.docker.internal`).
- `DB_NAME`: The database name (default: `gitea`).
- `DB_USER`: The database user (default: `gitea`).
- `DB_PASSWD`: The database password.

### Gitea Security Settings
- `INSTALL_LOCK`: Lock the installation (default: `true`).
- `REVERSE_PROXY_LIMIT`: Limit for reverse proxies (default: `1`).
- `PROXY_TRUSTED_PROXIES`: Trusted proxies (default: `172.16.0.0/12`).

### Gitea Server Settings
- `DOMAIN`: The domain for Gitea (default: `git.local.krislamo.org`).
- `SSH_PORT`: The SSH port (default: `127.0.0.1:222`).
- `WEB_PORT`: The web port (default: `127.0.0.1:3000`).

### Gitea Logging Settings
- `LOG_MODE`: The logging mode (default: `file`).

### Network Settings
- `NETWORK`: The network to be used (default: `traefik`).

## Static Configuration

### Extra Hosts
- `host.docker.internal:host-gateway` is defined for a host-run MariaDB instance

### Volumes
- `gitea:/data:rw`: Named volume for Gitea data.
- `/home/git/.ssh:/data/git/.ssh:rw`: SSH data.
- `/var/log/gitea:/data/gitea/log:rw`: Log data.
- `/etc/timezone:/etc/timezone:ro` and `/etc/localtime:/etc/localtime:ro`: Timezone data.

## License
This project is released under the 0BSD license, which allows for unrestricted
use, modification, and distribution.