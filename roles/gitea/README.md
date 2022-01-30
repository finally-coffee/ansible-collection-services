# `finallycoffee.services.gitea` ansible role

## Overview

This role deploys [gitea](https://gitea.com/)
using its official available docker image, and is able to setup SSH
forwarding from the host to the container (enabling git-over-SSH without
the need for a non-standard SSH port while running an SSH server on the
host aswell).

### Configuration

#### Email notifications

To enable to send emails, you need to set the following variables, demonstrated
here with an SMTP server. A TLS connection is strongly advised, as otherwise, it
can be trival to intercept a login to the mail server and record the authentication
details, enabling anyone to send mail as if they were your gitea instance.

```yaml
gitea_config_mailer_enabled: true
# Can be `sendmail` or `smtp`
gitea_config_mailer_type: smtp
# Including the port can be used to force secure smtp (SMTPS)
gitea_config_mailer_host: mail.my-domain.tld:465
gitea_config_mailer_user: gitea
gitea_config_mailer_passwd: very_long_password
gitea_config_mailer_tls: true
gitea_config_mailer_from_addr: "gitea@{{ gitea_domain }}"
# Set `gitea_config_mailer_sendmail_path` when using a sendmail binary
gitea_config_mailer_sendmail_path: /usr/sbin/sendmail
```

For more information, see [the gitea docs on email setup](https://docs.gitea.io/en-us/email-setup/).
