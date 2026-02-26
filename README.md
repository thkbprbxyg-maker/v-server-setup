# V-Server Setup Documentation

This repository documents the complete setup of a secure Linux V-Server environment including SSH configuration, security hardening, web server installation, and Git setup.

---

## Table of Contents

1. [Project Goal](#project-goal)
2. [Server Environment](#server-environment)
3. [SSH Key Configuration](#ssh-key-configuration)
4. [Disable Password Authentication](#disable-password-authentication)
5. [Web Server Installation](#web-server-installation)
6. [Git Configuration](#git-configuration)
7. [Security Notes](#security-notes)
8. [Checklist PDF](#checklist-pdf)

---

## Project Goal

This project configures a secure V-Server that can be used for deploying web applications.  
The server is hardened by disabling password authentication and enabling SSH key-based login.
---

## Server Environment

- Operating System: Ubuntu (or Debian-based Linux)
- Access Method: SSH
- Authentication: Public Key Authentication

---

## SSH Key Configuration

Steps:

1. Generate an SSH key locally (if not already existing).
2. Copy the public key to the server.
3. Add the public key to `~/.ssh/authorized_keys`.
4. Verify the login via:

```bash
ssh <user>@<server-ip>
```

## Disable Password Authentication

To improve security, password authentication is disabled:

1. Edit the SSH configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

2.Modified the following settings:

```bash
PasswordAuthentication no
PubkeyAuthentication yes
```

3.Restarted SSH service:

```bash
sudo systemctl restart ssh
```

## Web Server Installation

Install a web server to serve applications.
Example using nginx:

```bash
sudo apt update
sudo apt install nginx
```

Service was started and enabled:

```bash
sudo systemctl enable nginx
sudo systemctl start nginx
```

The installation was verified by accessing the server IP in a browser.

## Git Configuration

Install and configure Git on the server:

```bash
sudo apt install git
```

Configured global user settings:

```bash
git config --global user.name "<Your Name>"
git config --global user.email "<your@email.com>"
```

## Security Notes

- No passwords are stored in this repository.
- No private SSH keys are included.
- Only public key authentication is used.
- Password login is disabled on the server.
- This repository contains documentation only.

---

## Checklist PDF

The original checklist is included in this repository:

- [Checklist PDF](docs/checklist-v-server.pdf)