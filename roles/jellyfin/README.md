# `finallycoffee.services.jellyfin` ansible role

This role runs [Jellyfin](https://jellyfin.org/), a free software media system,
in a docker container.

## Usage

`jellyfin_domain` contains the FQDN which jellyfin should listen to. Most configuration
is done in the software itself.

Jellyfin runs in host networking mode by default, as that is needed for some features like
network discovery with chromecasts and similar.

Media can be mounted into jellyfin using `jellyfin_media_volumes`, taking a list of strings
akin to `community.docker.docker_container`'s `volumes` key.
