# `finallycoffee.services.hedgedoc` ansible role

Role to deploy and configure hedgedoc using `docker` or `podman`.
To configure hedgedoc, set either the config as complex data
directly in `hedgedoc_config` or use the flattened variables
from the `hedgedoc_config_*` prefix (see
[defaults/main/config.yml](defaults/main/config.yml)).

To remove hedgedoc, set `hedgedoc_state: absent`. Note that this
will delete all data directories aswell, removing any traces this
role created on the target (except database contents).

# Required configuration

- `hedgedoc_config_domain` - Domain of the hedgedoc instance
- `hedgedoc_config_session_secret` - session secret for hedgedoc

## Deployment methods

To set the desired deployment method, set `hedgedoc_deployment_method` to a
supported deployment methods (see [vars/main.yml](vars/main.yml#5)).
