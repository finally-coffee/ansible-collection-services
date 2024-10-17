# `finallycoffee.services.vaultwarden` ansible role

## Configuration

To use this role, the following variables need to be populated:

- `vaultwarden_config_domain` - always. Changing this will lead to two-factor not working for two-factor methods registered in the past.
- `vaultwarden_config_admin_token` - if `vaultwarden_config_disable_admin_token` is `false`.

### Email

Configure mailing by first enabling SMTP using `vaultwarden_config_enable_smtp: true`, then configure your email server like this:
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

To enable email-based two-factor-authentication, set `vaultwarden_config_enable_email_2fa: true` and optionally set the following configuration:
```yaml
vaultwarden_config:
  email_token_size: 8
  email_expiration_time: 300 # 300 seconds = 5min
  email_attempts_limit: 3
```

