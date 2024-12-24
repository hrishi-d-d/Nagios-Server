# Nagios-Server Infrastructure Monitoring

![Nagios Logo](https://github.com/hrishi-d-d/test/blob/main/download%20(9).png)

This project involves setting up **Nagios-Server infrastructure monitoring**, using a **Debian machine** as the server and a **Windows machine** as the client with the **Nagios Cross-Platform Agent (NCPA)**.
Here I have added the screenshots regarding the project.

## Overview
Nagios is a powerful monitoring system that allows you to track the performance and availability of IT infrastructure. In this project, we:
- Configure a Debian machine as the Nagios server.
- Install and configure the Nagios Cross-Platform Agent (NCPA) on a Windows client.
- Set up checks for CPU, memory, disk usage, and service statuses.

## Features
- Real-time monitoring of Windows client metrics.
- Centralized web interface for monitoring and alert management.
- Proactive detection of infrastructure issues.

## Prerequisites
- A Debian machine (server).
- A Windows machine (client).
- Basic knowledge of Linux commands.

## Setup Instructions

### Step 1: Install Nagios Core on Debian
1. Update your system:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. Install necessary dependencies:
   ```bash
   sudo apt install build-essential apache2 php libgd-dev unzip
   ```
3. Download and install Nagios Core:
   ```bash
   wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.x.tar.gz
   tar -xvf nagios-4.x.tar.gz
   cd nagios-4.x
   ./configure
   make all
   sudo make install
   ```
4. Start Nagios services:
   ```bash
   sudo systemctl start nagios
   ```

### Step 2: Install NCPA on Windows Client
1. Download the NCPA agent from the [official site](https://www.nagios.org/ncpa/).
2. Run the installer and follow the setup wizard.
3. Configure the `ncpa.cfg` file to allow the Nagios server to connect.
4. Start the NCPA Listener and Passive services.

### Step 3: Configure Nagios for Monitoring
1. Define the Windows host in `nagios.cfg`:
   ```bash
   sudo nano /usr/local/nagios/etc/nagios.cfg
   ```
2. Add the host and service configuration for the Windows client.
3. Restart Nagios:
   ```bash
   sudo systemctl restart nagios
   ```

## Usage
- Access the Nagios web interface at `http://<server-ip>/nagios`.
- View host and service statuses.
- Receive alerts for any detected issues.

## Troubleshooting
- Ensure the NCPA services are running on the Windows client.
- Verify firewall rules allow communication between the Debian server and Windows client.

## License
This project uses the [Nagios license](https://www.nagios.com/legal/licenses/).

---

**Happy Monitoring!**

