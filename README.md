# Nagios-Server Infrastructure Monitoring

![Nagios Logo](https://github.com/hrishi-d-d/test/blob/main/download%20(9).png)

This project involves setting up **Nagios-Server infrastructure monitoring**, using a **Debian machine** as the server, a **Windows machine**, and a second **Debian machine** as clients with the **Nagios Cross-Platform Agent (NCPA)**.

## Overview
Nagios is a powerful monitoring system that allows you to track the performance and availability of IT infrastructure. In this project, we:
- Configure a Debian machine as the Nagios server.
- Install and configure the Nagios Cross-Platform Agent (NCPA) on a Windows client and a second Debian client.
- Set up checks for CPU, memory, disk usage, and service statuses on all monitored machines.

## Features
- Real-time monitoring of metrics from multiple clients (Windows and Debian).
- Centralized web interface for monitoring and alert management.
- Proactive detection of infrastructure issues.

## Prerequisites
- A Debian machine (server).
- A Windows machine (client).
- A second Debian machine (client).
- Basic knowledge of Linux commands.

## Setup Instructions

### Step 1: Install Nagios Core on Debian Server
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

### Step 3: Install NCPA on Debian Client
1. Update your system:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. Install the NCPA agent:
   ```bash
   wget https://assets.nagios.com/downloads/ncpa/ncpa-<version>.tar.gz
   tar -xvf ncpa-<version>.tar.gz
   cd ncpa-<version>
   ./install
   ```
3. Configure the `ncpa.cfg` file to allow the Nagios server to connect.
4. Start the NCPA services:
   ```bash
   sudo systemctl start ncpa_listener
   sudo systemctl start ncpa_passive
   ```

### Step 4: Configure Nagios for Monitoring
1. Define the Windows and Debian hosts in `nagios.cfg`:
   ```bash
   sudo nano /usr/local/nagios/etc/nagios.cfg
   ```
2. Add host and service configurations for the Windows client and the second Debian client.
3. Restart Nagios:
   ```bash
   sudo systemctl restart nagios
   ```

## Usage
- Access the Nagios web interface at `http://<server-ip>/nagios`.
- View host and service statuses for all monitored machines.
- Receive alerts for any detected issues.

## Troubleshooting
- Ensure the NCPA services are running on both the Windows and Debian clients.
- Verify firewall rules allow communication between the Nagios server and clients.
