# `finallycoffee.services.pretix` ansible role

Deploy [pretix](https://pretix.eu) using ansible. Note that this
role does not configure pretix beyond its own configuration file,
and requires changing a default admin password after a successful
installation.

## Configuration

For all available configuration options, see [`defaults/main/config.yml`](defaults/main/config.yml)
and other supporting files in the [`defaults/main/`](defaults/main/) folder.

To add custom configuration to pretix, populate them in `pretix_config`,
where they will be (recusively) merged into the default configuration.

### Required

- `pretix_domain`: domain of the pretix instance
- `pretix_postgresql_password`: password for the (default: postgresql) database
- `pretix_config_redis_location`: connection string for the main pretix redis database
- `pretix_config_celery_backend`: connection string for the celery backend, can be a (different!) redis database
- `pretix_config_celery_broker`: connection string for the celery broker, can be a (yet another different) redis database

For examples on how a redis server (like valkey) can be configured
for redis, see [`playbooks/pretix.yml`](../../playbooks/pretix.yml).

### Mailing

Set up mails in pretix by populating the following variables:
- `pretix_config_mail_host`: domain/IP and optional port of the SMTP server
- `pretix_config_mail_user`: SMTP user to authenticate
- `pretix_config_mail_password`: password for the SMTP user

### Plugins

To install more plugins, list the wanted `pypi` packages as a list in
`pretix_plugins`. They will be installed in the created virtualenv, and migrations and an asset rebuild will be automatically started.

If your plugin requires custom configuration (f.ex.: `pretix-oidc`),
add the configuration into `pretix_config`.

## Troubleshooting

### virtualenv

By default, the virtualenv is located in `/var/lib/pretix/virtualenv`.
This can be controlled by setting `pretix_virtualenv_dir`.

NOTE: To fix a broken virtualenv, try setting `pretix_virtualenv_state` to `forcereinstall` (see
[`ansible.builtin.pip` on docs.ansible.com](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/pip_module.html)).

NOTE: To install pip packages or execute migrations in the virtualenv, ansible
needs to become the unprivilated `pretix_user` (default: `pretix`). This might
require having the `acl` system package installed.
