---
created: 2026-03-14
updated: 2026-03-14
tags:
  - area
  - area/personal
---

# Homelab

## Purpose

> Why does this area exist? What does "good" look like here on an ongoing basis?

Personal homelab infrastructure for running services and accessing my vault remotely.

---

## Current Status

*Last reviewed: 2026-03-14*

- New VM "obsidian" provisioned and running
- Tailscale configured for remote access
- OpenCode web service auto-starting via systemd

## Standards & Goals

> Not a project with an end date — these are ongoing commitments and benchmarks.

- Keep VM updated with security patches
- Maintain Tailscale connection for remote access
- Backup vault regularly

## Active Projects in This Area

```dataview
LIST
FROM "10 - Projects"
WHERE area = "Homelab"
SORT file.mtime DESC
```

## Key Resources & References

- VM: obsidian (Fedora)
- Services: OpenCode (v1.2.26, web mode), Tailscale
- Access: Tailscale VPN
- Systemd service: `/etc/systemd/system/opencode-web.service`

## Setup Instructions

### Prerequisites
- Fedora VM with sudo access
- GitHub account for OpenCode authentication

### 1. Install System Packages
```bash
sudo dnf install git
```

### 2. Install OpenCode
Download and install from [OpenCode releases](https://github.com/cooderl/opencode/releases):
```bash
# Download the latest binary to /usr/local/bin/opencode
chmod +x /usr/local/bin/opencode
opencode --version  # Verify installation
```

### 3. Setup SELinux Policy (if needed)
If you encounter SELinux denials when running OpenCode:
```bash
ausearch -c '(opencode)' --raw | audit2allow -M my-opencode
semodule -X 300 -i my-opencode.pp
/sbin/restorecon -v /usr/local/bin/opencode
```

### 4. Create OpenCode Systemd Service
Create `/etc/systemd/system/opencode-web.service`:
```ini
[Unit]
Description=OpenCode Web Server

[Service]
Type=simple
User=root
WorkingDirectory=/home/willem/obsidian
ExecStart=/usr/local/bin/opencode web --hostname 0.0.0.0
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Enable and start the service:
```bash
sudo systemctl daemon-reload
sudo systemctl enable opencode-web
sudo systemctl start opencode-web
sudo systemctl status opencode-web
```

### 5. Configure Firewall
Allow port 4096 (OpenCode web server) through firewalld:
```bash
sudo firewall-cmd --permanent --add-port=4096/tcp
sudo firewall-cmd --reload
sudo firewall-cmd --list-all  # Verify port is open
```

### 6. Install Tailscale
```bash
curl -fsSL https://tailscale.com/install.sh | sh
```

Connect to Tailscale (generates auth URL on first run):
```bash
sudo tailscale up
```

Or use an auth key directly (pre-authorized):
```bash
sudo tailscale up --auth-key=<YOUR_AUTH_KEY>
```

### Verification
- Check OpenCode is running: `sudo systemctl status opencode-web`
- Check Tailscale is connected: `tailscale status`
- Access vault from local: `http://localhost:3000`
- Access vault remotely via Tailscale IP

## Notes & Log

### 2026-03-14
- Set up new VM "obsidian" on Fedora
- Installed: git, tailscale, opencode (v1.2.26)
- Created systemd service for OpenCode web mode auto-start at `/etc/systemd/system/opencode-web.service`
- Configured firewall to allow port 4096/tcp for OpenCode web access
- Configured Tailscale for remote vault access via VPN
- Resolved SELinux policy issues with OpenCode binary
- Documented full setup procedure for reproducibility
