# BOTS v3 Data Ingestion into Splunk

## 1. Objective

The objective of this phase is to install and load the **Splunk Boss of the SOC (BOTS) v3 dataset** into the Ubuntu-based Splunk environment.

BOTS v3 provides realistic security data for practicing **SOC investigation, threat hunting, incident analysis, and MITRE ATT&CK mapping**.

---

## 2. Install BOTS v3

### 2.1 Download the Dataset

On the Ubuntu Splunk server, navigate to `/tmp`:

```bash
cd /tmp
```

Download the official BOTS v3 dataset:

```bash
wget https://botsdataset.s3.amazonaws.com/botsv3/botsv3_data_set.tgz
```

Check the downloaded file:

```bash
ls -lh botsv3_data_set.tgz
```

The dataset should be approximately **320 MB**.

---

### 2.2 Verify the Dataset Using MD5

Before extracting the dataset, verify its integrity using the official MD5 checksum.

Official MD5:

```text
d7ccca99a01cff070dff3c139cdc10eb
```

Run:

```bash
md5sum botsv3_data_set.tgz
```

Expected output:

```text
d7ccca99a01cff070dff3c139cdc10eb  botsv3_data_set.tgz
```

If the calculated MD5 matches the official checksum, the downloaded dataset is valid and can be used for the installation.

---

### 2.3 Check the Splunk Apps Directory

Before extracting the dataset, verify the Splunk application directory:

```bash
ls /opt/splunk/etc/apps
```

This directory contains the applications and supporting data used by the Splunk installation.

---

### 2.4 Extract BOTS v3 into Splunk

Extract the downloaded BOTS v3 archive directly into the Splunk applications directory:

```bash
sudo tar -xvzf /tmp/botsv3_data_set.tgz -C /opt/splunk/etc/apps/
```

The extraction process creates the required BOTS v3 application/data directories under:

```text
/opt/splunk/etc/apps/
```

---

### 2.5 Verify the BOTS Installation

Check whether the BOTS-related directory was created:

```bash
ls -lah /opt/splunk/etc/apps/ | grep bots
```

If the BOTS-related directory is displayed, the dataset has been successfully extracted into the Splunk environment.

---

## 3. Restart Splunk

After installing the BOTS v3 application/data, restart Splunk to load the new configuration:

```bash
sudo /opt/splunk/bin/splunk restart
```

Verify that Splunk is running:

```bash
sudo /opt/splunk/bin/splunk status
```

---

## 4. Verify BOTS v3 in Splunk

Open Splunk Web and navigate to:

```text
Search & Reporting
```

Run a basic search:

```spl
index=botsv3
```

If events are returned, the BOTS v3 dataset is available for investigation.

---

## 5. Check Event Volume

To determine the total number of events available in the BOTS v3 index:

```spl
index=botsv3
| stats count
```

This provides the total event count currently available in the index.

---

## 6. Identify Sourcetypes

Run:

```spl
index=botsv3
| stats count by sourcetype
| sort - count
```

This identifies the different types of security data contained in the dataset.

---

## 7. Identify Hosts

Run:

```spl
index=botsv3
| stats count by host
| sort - count
```

This provides an overview of the hosts represented in the BOTS v3 dataset.

---

## 8. Verify the Event Time Range

Run:

```spl
index=botsv3
| stats earliest(_time) as earliest latest(_time) as latest
```

This verifies the earliest and latest timestamps available in the dataset.

---

## 9. Review Sample Events

Run:

```spl
index=botsv3
| head 20
```

Review the returned events to confirm that the BOTS v3 data is searchable and contains security-related activity.

---

## 10. BOTS v3 Installation Completed

The BOTS v3 dataset has been downloaded, integrity-verified, extracted into the Splunk application directory, and made available for investigation.

The BOTS v3 dataset will now be used as the foundation for the SOC investigation phases:

```text
01 - Brute Force
02 - PowerShell
03 - Malware
04 - C2
05 - WebShell
06 - Exfiltration
07 - Lateral Movement
08 - Privilege Escalation
09 - Persistence
10 - Full Attack
```

Each investigation will include relevant **SPL queries, security events, evidence, screenshots, analysis, and findings**.
