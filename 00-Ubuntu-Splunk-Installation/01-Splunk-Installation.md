# Splunk Enterprise Installation on Ubuntu

## 1. Objective

The objective of this phase is to install and configure **Splunk Enterprise on Ubuntu** to create the SIEM environment used for the SOC investigation project.

## 2. Lab Architecture

```text
┌─────────────────────┐
│       Ubuntu        │
│                     │
│  Splunk Enterprise  │
│                     │
│  Splunk Web : 8000  │
│  Management : 8089  │
└─────────────────────┘
           │
           │
           ▼
    BOTS v3 Dataset
           │
           ▼
    Splunk Index/Search
```

## 3. Update Ubuntu

First, update the Ubuntu package repository.

```bash
sudo apt update
sudo apt upgrade -y
```

Verify the system information:

```bash
hostnamectl
```

## 4. Download Splunk Enterprise

Download the appropriate **Splunk Enterprise `.deb` package** for Ubuntu from the official Splunk download page.

After downloading the package, move to the directory containing the file:

```bash
cd ~/Downloads
```

Check the downloaded package:

```bash
ls -lh
```

## 5. Install Splunk

Install the downloaded Debian package:

```bash
sudo dpkg -i splunk-*.deb
```

If dependencies are required:

```bash
sudo apt --fix-broken install -y
```

Then verify the Splunk installation directory:

```bash
ls /opt/splunk
```

## 6. Start Splunk

Start Splunk for the first time:

```bash
sudo /opt/splunk/bin/splunk start --accept-license
```

During the first startup, create the Splunk administrator account.

## 7. Enable Splunk at Boot

Configure Splunk to start automatically when Ubuntu boots:

```bash
sudo /opt/splunk/bin/splunk enable boot-start
```

Start Splunk:

```bash
sudo systemctl start Splunkd
```

Check the service:

```bash
sudo systemctl status Splunkd
```

## 8. Access Splunk Web

Open a browser and access:

```text
http://<UBUNTU-IP>:8000
```

Example:

```text
http://192.168.x.x:8000
```

Log in using the Splunk administrator account created during installation.

## 9. Verify Splunk

From the Splunk Web interface, verify that:

* Splunk Web is accessible
* The administrator account works
* Splunk Search & Reporting is available
* The Splunk service is running

## 10. Verify from CLI

Run:

```bash
sudo /opt/splunk/bin/splunk status
```

The Splunk service should report that it is running.

## 11. Installation Completed

At this stage, Splunk Enterprise is installed and running on Ubuntu.

The next phase is to prepare and ingest the **BOTS v3 dataset** into Splunk.

See: [`02-BOTS-v3-Data-Ingestion.md`](./02-BOTS-v3-Data-Ingestion.md)
