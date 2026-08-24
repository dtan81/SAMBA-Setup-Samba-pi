# SAMBA Share Setup Script for Raspberry Pi

A robust, idempotent script to install and configure a Samba (SMB) share on Raspberry Pi OS.

## Features

- Installs and configures Samba
- Creates a dedicated share with proper permissions
- Supports both interactive and non-interactive modes
- Includes full uninstall mode (`-X`) with optional force (`-f`)
- Idempotent configuration (safe to re-run)
- Creates backups of `smb.conf` before modifying

## Requirements

- Raspberry Pi running Raspberry Pi OS
- Root/sudo access

## Usage

### Interactive Install (recommended)
```bash
sudo ./setup_samba_pi.sh
```

### Non-Interactive Install
```bash
sudo ./setup_samba_pi.sh -u ki5wtr -P 'YourSecurePassword' -d /home/ki5wtr/shared -s myshare
```

### Guest/Public Share
```bash
sudo ./setup_samba_pi.sh -g
```

### Uninstall
```bash
sudo ./setup_samba_pi.sh -X           # Interactive uninstall
sudo ./setup_samba_pi.sh -X -f        # Force uninstall (non-interactive)
```

## Options

| Option | Description | Default |
|--------|-------------|---------|
| `-u`   | Samba/UNIX username | `ki5wtr` |
| `-P`   | Samba password | Prompted if omitted |
| `-d`   | Directory to share | `/srv/samba/share` |
| `-s`   | Share name | `ki5wtr_share` |
| `-g`   | Enable guest access | Disabled |
| `-r`   | Read-only share | Writable |
| `-X`   | Uninstall mode | - |
| `-f`   | Force (non-interactive) with `-X` | - |
| `-h`   | Show help | - |

## Security Notes

- Avoid passing passwords on the command line when possible (visible in process list)
- The script creates backups of `/etc/samba/smb.conf` before changes
- Use strong passwords for the Samba user

## License

MIT License — see [LICENSE](LICENSE) for details.

## Author

Created by Dominic Tanner (KI5WTR) — dtan81

---

If you find this useful, consider giving it a ⭐ on GitHub!