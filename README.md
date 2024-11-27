# linux-apache-virtual-host-setup
A guide to setting up several Virtual Hosts in Apache on Linux, allowing you to host and serve multiple applications on different ports.

---

## Prerequisites
Before you begin, ensure you have:
- A Linux server with Apache installed.

---

## Steps to Configure Virtual Hosts

### Step 1: Create Directories for Each Application
Create directories to hold the files for each application:
```bash
sudo mkdir /var/www/app1
sudo mkdir /var/www/app2
sudo mkdir /var/www/app3

### Step 2: Create Configuration Files for Each Virtual Host
