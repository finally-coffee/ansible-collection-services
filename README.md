# `finallycoffee.service` ansible collection

## Overview

This ansible collection is used as a pool of roles with no clear assigned scope,
and serves as a catch-all for ansible roles which do not fit into a clear
concise area of concern.

## Roles

- [`roles/restic-s3`](roles/restic-s3/README.md): Manage backups using restic
  and persist them to an s3-compatible backend.

- [`roles/minio`](roles/minio/README.md): Deploy [min.io](https://min.io), an
  s3-compatible object storage server, using docker containers.

## License

[CNPLv7+](LICENSE.md): Cooperative Nonviolent Public License
