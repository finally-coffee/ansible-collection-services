# `finallycoffee.services.snipe_it` ansible role

[Snipe-IT](https://snipeitapp.com/) is an open-source asset management with
a powerful JSON-REST API. This ansible role deploys and configures Snipe-IT.

## Requirements

Snipe-IT requires a MySQL-Database like MariaDB and a working email service
for sending email. For installing and configuring MariaDB, see
[`finallycoffee.base.mariadb`](https://galaxy.ansible.com/ui/repo/published/finallycoffee/base/content/role/mariadb/).

## Configuration

Required variables to set are:

- `snipe_it_domain` - domain name of the snipe-it instance
- `snipe_it_config_app_url` - URL where snipe-it will be reachable including protocol and port
- `snipe_it_config_app_key` - Laravel application key

### Database configuration

All (database) options from the upstream laravel `.env` file are available
under the `snipe_it_config_db_*` prefix. Configure a database as follows:
```
snipe_it_config_db_host: localhost # defaults to localhost
snipe_it_config_db_port: "3306" # defaults to 3306
snipe_it_config_db_database: my_snipe_db_name # defaults to 'snipeit'
snipe_it_config_db_username: my_snipe_db_user # defaults to 'snipeit'
snipe_it_config_db_password: my_snipe_db_password
# Set this if the database is shared with
# other applications. defaults to not set
snipe_it_config_db_prefix: snipe_
```

### Email configuration

Configuring an email server is mandatory. An example is provided below:
```yaml
snipe_it_config_mail_host: smtp.example.com
snipe_it_config_mail_username: snipe_user@snipe.example.com
snipe_it_config_mail_password: i_want_to_be_strong_and_long
snipe_it_config_mail_from_addr: "noreply@snipe.example.com"
snipe_it_config_mail_from_name: "Example.com SnipeIT instance"
```

The default smtp port is `587` and can be set in `snipe_it_config_mail_port`.
