# `finallycoffee.services.openproject` ansible role

Deploys [openproject](https://www.openproject.org/) using docker-compose.

## Configuration

To set configuration variables for OpenProject, set them in `openproject_compose_overrides`:
```yaml
openproject_compose_overrides:
  version: "3.7"
  services:
    proxy:
       [...]
  volumes:
    pgdata:
      driver: local
      driver_opts:
        o: bind
        type: none
        device: /var/lib/postgresql
```
