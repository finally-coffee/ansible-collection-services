# `finallycoffee.services.vouch-proxy`

[Vouch-Proxy](https://github.com/vouch/vouch-proxy) can be used in combination with
nginx' `auth_request` module to secure web services with OIDC/OAuth. This role runs
vouch-proxys' official docker container.

## Usage

The `oauth` config section must be supplied in `vouch_proxy_oauth_config`, and the
`vouch` config section can be overridden in `vouch_proxy_vouch_config`. For possible
configuration values, see https://github.com/vouch/vouch-proxy/blob/master/config/config.yml_example.

For an example nginx config, see https://github.com/vouch/vouch-proxy#installation-and-configuration.

Passing container arguments in the same way as `community.docker.docker_container` is supported
using the `vouch_proxy_container_[...]` prefix (e.g. `vouch_proxy_container_ports`).
