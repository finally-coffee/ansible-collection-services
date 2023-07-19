# `finallycoffee.services.ghost` ansible role

[Ghost](https://ghost.org/) is a self-hosted blog with rich media capabilities,
which this role deploys in a docker container.

## Requirements

Ghost requires a MySQL-database (like mariadb) for storing it's data, which
can be configured using the `ghost_database_(host|username|password|database)` variables.

Setting `ghost_domain` to a fully-qualified domain on which ghost should be reachable
is also required.

Ghosts configuration can be changed using the `ghost_config` variable.

Container arguments which are equivalent to `community.docker.docker_container` can be
provided in the `ghost_container_[...]` syntax (e.g. `ghost_container_ports` to expose
ghosts port to the host).
