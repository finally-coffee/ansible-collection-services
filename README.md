# `finallycoffee.service` ansible collection

## Overview

This ansible collection is used as a pool of roles with no clear assigned scope,
and serves as a catch-all for ansible roles which do not fit into a clear
concise area of concern.

## Roles

- [`roles/gitea`](roles/gitea/README.md): Deploy [gitea.io](https://gitea.io), a
  lightweight, self-hosted git service.

- [`roles/jellyfin`](roles/jellyfin/README.md): Deploy [jellyfin.org](https://jellyfin.org),
  the free software media system for streaming stored media to any device.

- [`roles/restic`](roles/restic/README.md): Manage backups using restic
  and persist them to a configurable backend.

- [`roles/minio`](roles/minio/README.md): Deploy [min.io](https://min.io), an
  s3-compatible object storage server, using docker containers.

## License

[CNPLv7+](LICENSE.md): Cooperative Nonviolent Public License
