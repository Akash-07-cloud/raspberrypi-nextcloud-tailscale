#  Raspberry Pi Nextcloud Server with Tailscale Remote Access

A self-hosted private cloud storage server built using **Raspberry Pi**, **Nextcloud**, and **Tailscale VPN** to enable secure access from anywhere without port forwarding or exposing public IP.

---

##  Project Overview

This project demonstrates how to build a **personal cloud storage system** similar to Google Drive using open-source tools.

The Raspberry Pi hosts a Nextcloud server locally, while Tailscale creates a secure private network so users can access the cloud from any device anywhere in the world.

This setup is ideal for:

* Secure file sharing
* Private team storage
* Remote access without router configuration
* Learning self-hosting and networking

---

# Key Features

* ✔ Self-hosted cloud on Raspberry Pi
* ✔ Secure remote access using Tailscale VPN
* ✔ No public IP exposure
* ✔ No port forwarding required
* ✔ Works across mobile, Windows, Linux, and macOS
* ✔ Team access using shared tailnet account
* ✔ Fully open-source stack

---

##  Tech Stack

* **Hardware:** Raspberry Pi
* **OS:** Debian Linux (Raspberry Pi OS)
* **Server:** Apache + PHP + MySQL
* **Cloud Platform:** Nextcloud
* **Secure Networking:** Tailscale VPN
* **Storage:** External SSD / NAS drive

---

##  System Architecture

```
User Device (Phone / Laptop)
        │
        ▼
   Tailscale VPN Network
        │
        ▼
  Raspberry Pi Server
        │
        ▼
     Nextcloud Web App
        │
        ▼
   Local SSD Storage
```

---

##  Installation Steps

### 1️ Install Nextcloud on Raspberry Pi

```
sudo apt update
sudo apt install apache2 mariadb-server php php-mysql php-gd php-curl php-xml php-zip php-mbstring unzip -y
```

Download Nextcloud:

```
wget https://download.nextcloud.com/server/releases/latest.zip
unzip latest.zip
sudo mv nextcloud /var/www/
sudo chown -R www-data:www-data /var/www/nextcloud
```

---

### 2️ Configure Apache

Enable required modules:

```
sudo a2enmod rewrite headers env dir mime
sudo systemctl restart apache2
```

Access locally:

```
http://localhost
```

---

### 3️⃣ Install Tailscale

```
curl -fsSL https://tailscale.com/install.sh | sh
sudo systemctl enable --now tailscaled
sudo tailscale up
```

Login using your Google account when prompted.

---

### 4️⃣ Access Nextcloud Remotely

Find Tailscale IP:

```
tailscale ip -4
```

Open in browser:

```
http://<tailscale-ip>
```

Example:

```
http://100.xxx.xxx.xxx
```

---

## 🎯 Learning Outcomes

* Self-hosting web applications
* Linux server configuration
* VPN networking fundamentals
* Secure remote access architecture
* Storage server deployment
* Cloud alternative implementation

---

## 🚀 Future Improvements

* HTTPS using Tailscale certificates
* Automated backups
* User quota management
* Domain integration
* Docker containerization
* RAID storage expansion

---

## 👨‍💻 Author

**Akash**
Electronics & Communication Engineering Student
Passionate about Embedded Systems, Networking & Self-Hosting

---

## ⭐ If you like this project

Give it a ⭐ on GitHub and feel free to fork or improve!
