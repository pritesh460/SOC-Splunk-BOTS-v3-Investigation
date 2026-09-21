# Ubuntu Splunk Installation & BOTS v3 Setup

This section documents the setup of the **Splunk SIEM environment on Ubuntu** and the ingestion of the **Splunk BOTS v3 dataset** for SOC investigation and threat-hunting practice.

## Objectives

* Install Splunk Enterprise on Ubuntu
* Configure Splunk for SOC investigations
* Download and prepare the BOTS v3 dataset
* Ingest BOTS v3 data into Splunk
* Verify that the data is searchable
* Prepare the environment for incident investigations

## Lab Environment

| Component        | Details                            |
| ---------------- | ---------------------------------- |
| SIEM             | Splunk Enterprise                  |
| Operating System | Ubuntu                             |
| Dataset          | Splunk BOTS v3                     |
| Purpose          | SOC Investigation & Threat Hunting |

## Setup Workflow

```text
Ubuntu
   ↓
Install Splunk Enterprise
   ↓
Configure Splunk
   ↓
Download BOTS v3 Dataset
   ↓
Create Splunk Index
   ↓
Ingest BOTS v3 Data
   ↓
Verify Data
   ↓
SOC Investigation
```

## Documentation

### 01 — Splunk Installation

Documents the complete process of installing and configuring Splunk Enterprise on Ubuntu.

See: [`01-Splunk-Installation.md`](./01-Splunk-Installation.md)

### 02 — BOTS v3 Data Ingestion

Documents the process of preparing the BOTS v3 dataset and ingesting it into Splunk for investigation.

See: [`02-BOTS-v3-Data-Ingestion.md`](./02-BOTS-v3-Data-Ingestion.md)

## Next Step

After completing the Splunk installation and BOTS v3 data ingestion, the environment will be ready for the **10 SOC incident investigations**.

