# `finallycoffee.service` ansible collection

## Overview

This ansible collection is used as a pool of roles with no clear assigned scope,
and serves as a catch-all for ansible roles which do not fit into a clear
concise area of concern.

## Roles

- [`roles/authelia`](roles/authelia/README.md): Deploys an [authelia.com](https://www.authelia.com)
  instance, an authentication provider with beta OIDC provider support.

- [`roles/gitea`](roles/gitea/README.md): Deploy [gitea.io](https://gitea.io), a
  lightweight, self-hosted git service.

- [`roles/jellyfin`](roles/jellyfin/README.md): Deploy [jellyfin.org](https://jellyfin.org),
  the free software media system for streaming stored media to any device.

- [`roles/restic`](roles/restic/README.md): Manage backups using restic
  and persist them to a configurable backend.

## License

[CNPLv7+](LICENSE.md): Cooperative Nonviolent Public License
