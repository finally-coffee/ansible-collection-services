# `finallycoffee.service` ansible collection

## Overview

This ansible collection is used as a pool of roles with no clear assigned scope,
and serves as a catch-all for ansible roles which do not fit into a clear
concise area of concern.

## Roles

- [`authelia`](roles/authelia/README.md): Deploys an [authelia.com](https://www.authelia.com)
  instance, an authentication provider with beta OIDC provider support.

- [`ghost`](roles/ghost/README.md): Deploys [ghost.org](https://ghost.org/), a simple to use
  blogging and publishing platform.

- [`gitea`](roles/gitea/README.md): Deploy [gitea.io](https://gitea.io), a
  lightweight, self-hosted git service.

- [`hedgedoc`](roles/hedgedoc/README.md): Deploy [hedgedoc](https://hedgedoc.org/),
  a collaborative real-time markdown editor using websockts

- [`jellyfin`](roles/jellyfin/README.md): Deploy [jellyfin.org](https://jellyfin.org),
  the free software media system for streaming stored media to any device.

- [`openproject`](roles/openproject/README.md): Deploys an [openproject.org](https://www.openproject.org)
  installation using the upstream provided docker-compose setup.

- [`vaultwarden`](roles/vaultwarden/README.md): Deploy [vaultwarden](https://github.com/dani-garcia/vaultwarden/),
  an open-source implementation of the Bitwarden Server (formerly Bitwarden\_RS).

- [`vouch_proxy`](roles/vouch_proxy/README.md): Deploys [vouch-proxy](https://github.com/vouch/vouch-proxy),
  an authorization proxy for arbitrary webapps working with `nginx`s' `auth_request` module.

## License

[CNPLv7+](LICENSE.md): Cooperative Nonviolent Public License
