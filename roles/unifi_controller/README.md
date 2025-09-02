# `finallycoffee.services.unifi_controller` ansible role

Deploy [`jacobalberty/unifi-docker`](https://github.com/jacobalberty/unifi-docker)
using either `docker` or `podman` (configure using
`unifi_controller_deployment_method`).

## Configuration

Change the default bind IP of `::` by setting
`unifi_controller_bind_ip`. By default, the ports
`1900/udp` (SSDP), `3478/udp` (STUN), `10001/udp`,
`8080/tcp` (HTTP), `8443/tcp` (HTTPS) and `6789/tcp`
are exposed.

For more information on which ports are needed when, see
[Unifi's required ports reference](https://help.ui.com/hc/en-us/articles/218506997-Required-Ports-Reference).
