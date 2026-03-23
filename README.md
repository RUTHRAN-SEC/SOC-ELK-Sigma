# SOC-ELK-Sigma

![Docker](https://img.shields.io/badge/Docker-Ready-blue)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-8-yellow)
![Kibana](https://img.shields.io/badge/Kibana-8-orange)
![Sigma](https://img.shields.io/badge/Sigma-Detection-red)

## Overview
**SOC-ELK-Sigma** is a professional SOC pipeline built using the **ELK Stack** (Elasticsearch, Logstash, Kibana) and **Sigma rules** for threat detection.  
It ingests Linux authentication logs, detects attacks like SSH brute force, triggers alerts, and visualizes events in Kibana dashboards.

This project demonstrates **real SOC skills**, including log ingestion, detection engineering, alerting, and dashboard creation perfect for a junior SOC analyst or detection engineer portfolio.

---

## Features
- Collects and parses Linux logs via Logstash  
- Stores logs in Elasticsearch for fast search  
- Detects threats using Sigma rules (SSH brute-force example included)  
- Automated alerting in Kibana  
- Visual dashboards for real-time SOC monitoring  
- Fully containerized with Docker for easy deployment  

---

## Architecture

```text
[Linux Host Logs] --> [Logstash] --> [Elasticsearch] --> [Kibana Dashboard]
                                \
                                 --> [Sigma Rules Detection]
```
## Screenshots

### Failed SSH login attempts:
<img width="711" height="400" alt="image" src="https://github.com/user-attachments/assets/33fa7be1-d14b-4c47-90d2-c73b5d44e837" />

### Top attacking IPs:
<img width="1158" height="749" alt="image" src="https://github.com/user-attachments/assets/31653374-0cd5-417e-a85d-d7ff646cbb65" />

## Installation
### Prerequisites
- Docker & Docker Compose installed
- Linux host with authentication logs (/var/log/auth.log)

## Steps
### Clone the repository
```
git clone https://github.com/RUTHRAN-SEC/SOC-ELK-Sigma.git

```

### Move to SOC-ELK-Sigma
```
cd SOC-ELK-Sigma
```

### Start ELK stack + Logstash
```
sudo docker-compose down && sudo docker-compose up -d
```
### Access Kibana:
```
http://localhost:5601
```

## Usage
- Logs are automatically ingested via Logstash
- Sigma detection rules are in sigma_rules/
- Logstash configuration is in logstash_pipeline/logstash.conf
- Kibana dashboards visualize attacks in real time
- Alerts are automatically generated for matching detection rules
- Example Detection (Sigma Rule)

## SSH Brute Force Detection
```
title: SSH Brute Force Detection
description: Detects multiple failed SSH login attempts
logsource:
  product: linux
  service: sshd
detection:
  selection:
    log_message: "Failed password"
  condition: selection
level: high

- Converts to Elasticsearch query via Sigmac
- Triggers alerts in Kibana if threshold exceeded
```

## Contributing
- Open an issue or pull request for improvements
- Add more Sigma rules for additional detections
- Extend dashboards with new visualizations

## DONE BY
### RUTHRAN-SEC
