# tarsnap-periodic
Scripts for tarsnap backups with periodic on FreeBSD.

All credit goes to [ross/zfs-periodic](https://github.com/ross/zfs-periodic) -- I did little beyond `sed s/zfs snapshot/tarsnap/`.

Install from ports: `sysutils/tarsnap-periodic`.

In order to enable periodic tarsnap backups you need
to add these lines to your `/etc/periodic.conf`:

```sh
daily_tarsnap_backup_enable="YES"
daily_tarsnap_backup_paths="/"
daily_tarsnap_backup_keep=7
weekly_tarsnap_backup_enable="YES"
weekly_tarsnap_backup_paths="/"
weekly_tarsnap_backup_keep=5
monthly_tarsnap_backup_enable="YES"
monthly_tarsnap_backup_paths="/"
monthly_tarsnap_backup_keep=2
```

Note: The first tarsnap backup can take a very long time. Therefore it might be a good idea to run it by hand and let it finish before turning on these scripts. Further backups will be incremental, so they shouldn't take that long.
