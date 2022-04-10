# `finallycoffee.services.authelia` ansible role

Deploys [authelia](https://www.authelia.com), an open-source full-featured
authentication server with OIDC beta support.

## Configuration

Most configurations options are exposed to be overrideable by setting
`authelia_config_{flat_config_key}`, which means `totp.digits: 8`
would become `authelia_config_totp_digits: 8`.

If configuration is not exposed in [`defaults/main.yml`](defaults/main.yml),
it can be overridden in `authelia_extra_config`, which is merged recursively
to the default config. Entire blocks can currently not be easily overridden,
it's best to rely on the `authelia_extra_config` here.

Below are some configuration hints towards enabling 2nd factor
providers like TOTP, WebAuthN etc.

### TOTP

See [the authelia docs on TOTP](https://www.authelia.com/docs/configuration/one-time-password.html#algorithm)
before adjusting some of the fine-grained configuration, as many
TOTP clients do not properly support all by-spec supported values.

```yaml
authelia_config_totp_disable: false
authelia_config_totp_issuer: "your.authelia.domain"
# Best to stick to authelias guide here
authelia_config_totp_algorithm: [...]
authelia_config_totp_digits: [...]
authelia_config_totp_period: [...]
```

### WebAuthN

```yaml
authelia_config_webauthn_disable: false
authelia_config_webauthn_timeout: 30s
# Force user to touch the security key's confirmation button
authelia_config_webauthn_user_verification: required
```

For more information about possible WebAuthN configuration, see
[the authelia docs on WebAuthN](https://www.authelia.com/docs/configuration/webauthn.html).

### Database & Redis

While Authelia can use a sqlite DB with in memory store by setting
`authelia_sqlite_storage_file_path`, it is recommended to use a proper
database and a redis instance:
```yaml
authelia_database_type: postgres
authelia_database_host: /var/run/postgres/
authelia_database_user: authelia
authelia_database_pass: authelia

# Redis
authelia_redis_host: /var/run/redis/
authelia_redis_pass: very_long_static_secret

```

### Notifications

For a test setup, notifications can be written into a config file, this behaviour
is enabled by setting `authelia_config_notifier_filesystem_filename`. For real-world
use, an SMTP server is strongly recommended, its config is as follows:
```
authelia_smtp_host: mail.domain.com
authelia_smtp_port: 587 # for StartTLS
authelia_smtp_user: authelia@domain.com
authelia_smtp_pass: authelia_user_pass
```
