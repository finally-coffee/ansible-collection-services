# `finallycoffee.services.keycloak` ansible role

Ansible role for deploying keycloak, currently only supports docker.

Migrated from `entropia.sso.keycloak`.

## Required variables

- `keycloak_database_password` - password for the database user
- `keycloak_config_hostname` - public domain of the keycloak server

## Database configuration

- `keycloak_database_hostname` - hostname of the database server, defaults to `localhost`
- `keycloak_database_username` - username to use when connecting to the database server, defaults to `keycloak`
- `keycloak_database_database` - name of the database to use, defaults to `keycloak`
