# `finallycoffee.services.vaultwarden` ansible role

Vaultwarden is an unofficial (not associated with Bitwarden) bitwarden API compatible
server backend, formally called `bitwarden_rs`, written in rust.

This ansible role can deploy and configure `vaultwarden`, and supports removing
itself using `vaultwarden_state: absent` (Warning: It does not ask for confirmation,
and will remove all user data when instructed to remove it).

## Configuration

To use this role, the following variables need to be populated:

- `vaultwarden_config_domain` - always. Changing this will lead to two-factor not working for two-factor methods registered in the past.
- `vaultwarden_config_admin_token` - if `vaultwarden_config_disable_admin_token` is `false`.

Setting other configuration values for vaultwarden can be done using role-provided flattened keys in the
`vaultwarden_config_*` namespace (see [`defaults/main/config.yml`](defaults/main/config.yml) for available variables),
or by setting the configuration directly in the same structure as the `config.json` would be in `vaultwarden_config`.

### Email

Configure mailing by first enabling SMTP using `vaultwarden_config_enable_smtp: true`,
then configure your email server like this:
```yaml
vaultwarden_config:
  smtp_host: "mail.example.com"
  smtp_explicit_tls: true
  smtp_port: 465
  smtp_from: "noreply+vaultwarden@example.com"
  smtp_from_name: "'Example.com Vaultwarden instance' <noreply+vaultwarden@example.com>"
  smtp_username: vaultwarden@example.com
  smtp_password: i_hope_i_will_be_a_strong_one!
  helo_name: "{{ vaultwarden_config_domain }}"
```

### 2FA via email

To enable email-based two-factor-authentication, set `vaultwarden_config_enable_email_2fa: true`
and optionally set the following configuration:
```yaml
vaultwarden_config:
  email_token_size: 8
  email_expiration_time: 300 # 300 seconds = 5min
  email_attempts_limit: 3
```

### Feature flags

To enable more authentication methods, toggles are provided in
[`vaultwarden_config_enable_*`](defaults/main/config.yml#L18).
It is genereally recommended to simply keep unused methods off.

Per default, 'Sends' are allowed.
