
# UFW (Uncomplicated Firewall) Guide for Linux

UFW is a user-friendly cli for managing firewall rules on Linux systems. It simplifies the process of creating an effective firewall for your server or desktop.

### Ubuntu/Debian
UFW usually comes pre-installed. If not:
```bash
sudo apt update
sudo apt install ufw
```

## Basic Usage

### Enable UFW
```bash
sudo ufw enable
```

### Disable UFW
```bash
sudo ufw disable
```

### Check Status
```bash
sudo ufw status
```

### Check Detailed Status
```bash
sudo ufw status verbose
```

## Allowing and Denying Connections

### Allow Specific Port
```bash
sudo ufw allow 22        # Allow SSH
sudo ufw allow 80        # Allow HTTP
sudo ufw allow 443       # Allow HTTPS
```

### Allow with Protocol
```bash
sudo ufw allow 53/udp    # Allow DNS
sudo ufw allow 25/tcp    # Allow SMTP
```

### Allow Port Range
```bash
sudo ufw allow 1000:2000/tcp
```

### Allow from Specific IP
```bash
sudo ufw allow from 192.168.1.100
```

### Allow from IP to Specific Port
```bash
sudo ufw allow from 192.168.1.100 to any port 22
```

### Deny Access
```bash
sudo ufw deny 23        # Deny Telnet
sudo ufw deny from 203.0.113.1
```

### Reject Access (More Explicit than Deny)
```bash
sudo ufw reject from 203.0.113.1
```

## Advanced Rules

### Limit SSH (helps prevent brute-force attacks)
```bash
sudo ufw limit ssh
```

### Delete a Rule
```bash
sudo ufw delete allow 22
```

### Reset UFW (Removes all rules)
```bash
sudo ufw reset
```

## Default Policies

### Set Default Policies (run before enabling)
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

## Viewing Rules (Numbered)
```bash
sudo ufw status numbered
```

## Application Profiles (for Ubuntu)

### List Available Application Profiles
```bash
sudo ufw app list
```

### Get Info on a Profile
```bash
sudo ufw app info OpenSSH
```

### Allow by Application Profile
```bash
sudo ufw allow OpenSSH
```

---

## Example: Basic Server Setup

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
sudo ufw status
```

---

## Additional Tips

- UFW rules are persistent after reboot.
- Always ensure SSH access is allowed **before** enabling UFW on a remote server.
- Use `ufw reload` to reapply rules if editing configuration files manually.

---

## Resources

- Official Docs: https://manpages.ubuntu.com/manpages/latest/en/man8/ufw.8.html
- Ubuntu Wiki: https://help.ubuntu.com/community/UFW
