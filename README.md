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

The goal of this project was to configure a secure V-Server that can be used for deploying web applications.  
The server was hardened by disabling password authentication and enabling SSH key-based login.

---

## Server Environment

- Operating System: Ubuntu (or Debian-based Linux)
- Access Method: SSH
- Authentication: Public Key Authentication

---

## SSH Key Configuration

Steps performed:

1. Generated an SSH key locally (if not already existing).
2. Copied the public key to the server.
3. Added the public key to `~/.ssh/authorized_keys`.
4. Verified successful login via:

```bash
ssh user@server-ip

##Disable Password Authentication

To improve security, password authentication was disabled:

1.Edited SSH configuration file:

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

##Web Server Installation

A web server was installed to serve applications:

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

##Git Configuration

Git was installed and configured on the server:

```bash
sudo apt install git
```

Configured global user settings:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

##Security Notes
 - No passwords are stored in this repository.
 - No private SSH keys are included.
 - Only documentation of the setup process is provided.






