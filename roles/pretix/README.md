# `finallycoffee.services.pretix` ansible role


## Troubleshooting

### virtualenv

By default, the virtualenv is located in `/var/lib/pretix/virtualenv`.
This can be controlled by setting `pretix_virtualenv_dir`.

NOTE: To fix a broken virtualenv, try setting `pretix_virtualenv_state` to `forcereinstall` (see
[`ansible.builtin.pip` on docs.ansible.com](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/pip_module.html)).

NOTE: To install pip packages or execute migrations in the virtualenv, ansible
needs to become the unprivilated `pretix_user` (default: `pretix`). This might
require having the `acl` system package installed.
