# `finallycoffee.services.restic-s3`

Ansible role for backup up data using `restic` to an `s3`-compatible backend,
utilizing `systemd` timers for scheduling

## Overview

The s3 repository and the credentials for it are specified in `restic_repo_url`,
`restic_s3_key_id` and `restic_s3_access_key`. As restic encrypts the data before
storing it, the `restic_repo_password` needs to be populated with a strong key,
and saved accordingly as only this key can be used to decrypt the data for a restore!

### Backing up data

A job name like `$service-postgres` or similar needs to be set in `restic_job_name`,
which is used for naming the `systemd` units, their syslog identifiers etc.

If backing up filesystem locations, the paths need to be specified in
`restic_backup_paths` as lists of strings representing absolute filesystem
locations.

If backing up f.ex. database or other data which is generating backups using
a command like `pg_dump`, use `restic_backup_stdin_command` (which needs to output
to `stdout`) in conjunction with `restic_backup_stdin_command_filename` to name
the resulting output (required).

### Policy

The backup policy can be adjusted by overriding the `restic_policy_keep_*`
variables, with the defaults being:

```yaml
restic_policy_keep_all_within: 1d
restic_policy_keep_hourly: 6
restic_policy_keep_daily: 2
restic_policy_keep_weekly: 7
restic_policy_keep_monthly: 4
restic_policy_backup_frequency: hourly
```

**Note:** `restic_policy_backup_frequency` must conform to `systemd`s
`OnCalendar` syntax, which can be checked using `systemd-analyze calender $x`.

## Role behaviour

Per default, when the systemd unit for a job changes, the job is not immediately
started. This can be overridden using `restic_start_job_on_unit_change: true`,
which will immediately start the backup job if it's configuration changed.

The systemd unit runs with `restic_user`, which is root by default, guaranteeing
that filesystem paths are always readable. The `restic_user` can be overridden,
but care needs to be taken to ensure the user has permission to read all the
provided filesystem paths / the backup command may be executed by the user.

If ansible should create the user, set `restic_create_user` to `true`, which
will attempt to create the `restic_user` as a system user.

### Installing

For Debian and RedHat, the role attempts to install restic using the default
package manager's ansible module (apt/dnf). For other distributions, the generic
`package` module tries to install `restic_package_name` (default: `restic`),
which can be overridden if needed.
