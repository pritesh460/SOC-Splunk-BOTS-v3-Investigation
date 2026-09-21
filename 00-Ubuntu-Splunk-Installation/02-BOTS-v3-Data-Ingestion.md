# BOTS v3 Data Ingestion into Splunk

## 1. Objective

The objective of this phase is to ingest the **Splunk BOTS v3 dataset** into the Ubuntu-based Splunk environment.

BOTS v3 provides security-related data that can be used to practice realistic SOC investigation, threat hunting, incident analysis, and MITRE ATT&CK mapping.

## 2. Dataset

The **Splunk Boss of the SOC (BOTS) v3** dataset is used as the primary investigation dataset for this project.

The dataset has already been downloaded and is available for ingestion.

## 3. Prepare the Dataset

First, identify the location of the downloaded BOTS v3 files.

Example:

```bash
cd ~/Downloads
ls -lh
```

If the dataset is compressed, extract it using the appropriate command.

For a `.tar.gz` archive:

```bash
tar -xvzf <bots-v3-file>.tar.gz
```

For a `.zip` archive:

```bash
unzip <bots-v3-file>.zip
```

Verify the extracted files:

```bash
ls -lh
```

## 4. Create a Dedicated Splunk Index

Open Splunk Web:

```text
Settings → Indexes → New Index
```

Create an index dedicated to the BOTS v3 dataset.

Example:

```text
Index Name: botsv3
```

Save the index.

## 5. Add BOTS v3 Data

Navigate to:

```text
Settings → Add Data
```

Select the appropriate data source according to the format of the downloaded BOTS v3 dataset.

Configure the destination index:

```text
Index: botsv3
```

Complete the data input configuration.

## 6. Verify Data Ingestion

Open:

```text
Search & Reporting
```

Run:

```spl
index=botsv3
```

If events are returned, the BOTS v3 data has been successfully ingested.

## 7. Check Event Volume

Run:

```spl
index=botsv3
| stats count
```

This provides the total number of events currently available in the index.

## 8. Identify Sourcetypes

Run:

```spl
index=botsv3
| stats count by sourcetype
| sort - count
```

This helps identify the different types of security data available in the dataset.

## 9. Identify Hosts

Run:

```spl
index=botsv3
| stats count by host
| sort - count
```

This provides an overview of the systems represented in the dataset.

## 10. Verify Time Range

Run:

```spl
index=botsv3
| stats earliest(_time) as earliest latest(_time) as latest
```

This verifies the time range of the ingested events.

## 11. Basic Investigation Search

Run:

```spl
index=botsv3
| head 20
```

Review the returned events and confirm that the dataset is searchable.

## 12. Data Ingestion Completed

The BOTS v3 dataset is now available in Splunk and can be used for SOC investigations.

The next phase of the project will investigate individual security incidents:

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

Each incident will have its own investigation, SPL queries, evidence, screenshots, and findings.
