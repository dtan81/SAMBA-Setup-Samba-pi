```markdown
# SAMBA Share Setup Script

This repository contains a single script to install and configure a Samba (SMB) share on a Raspberry Pi (Raspberry Pi OS). The script creates a dedicated share, adds an idempotent share block to /etc/samba/smb.conf, and can also uninstall and clean up everything it created.

Key features:
- Installs Samba (samba, samba-common-bin).
- Creates a system user `ki5wtr` by default (configurable).
- Adds a marked share block to /etc/samba/smb.conf (idempotent; removes previous script-managed block).
- Sets directory ownership/permissions appropriately.
- Adds Samba password for the user (via smbpasswd).
- Uninstall mode (-X) optionally removes smb entries, system user, data, and purges packages. Use -f for non-interactive full removal.

Usage examples:
- Interactive install (default):
  sudo ./setup_samba_pi.sh

- Non-interactive install:
  sudo ./setup_samba_pi.sh -u ki5wtr -P 'MyS3cureP@ss' -d /home/ki5wtr/shared -s myshare

- Guest/public share:
  sudo ./setup_samba_pi.sh -g

- Uninstall (interactive):
  sudo ./setup_samba_pi.sh -X

- Uninstall (non-interactive, force everything):
  sudo ./setup_samba_pi.sh -X -f

Script options:
- -u username (default: ki5wtr)
- -P samba password
- -d share directory (default: /srv/samba/share)
- -s share name (default: ki5wtr_share)
- -g guest share (no samba user)
- -r read-only
- -X uninstall mode
- -f force (non-interactive) with -X
- -h help

Security notes:
- Avoid passing passwords on command line if possible (they can be visible in process listings). Use interactive prompts where feasible.
- The script writes a backup of /etc/samba/smb.conf before modifying it (smb.conf.bak.TIMESTAMP).

License:
This project is MIT licensed — see LICENSE for details.
