# KQL SOC Investigation Lab

A hands-on Security Operations Center (SOC) investigation project using KQL, Microsoft Azure, and ServiceNow.

## Project Overview

This project simulates a real-world SOC investigation involving suspicious authentication activity, PowerShell execution, privilege escalation, and outbound network communication.

The investigation follows the workflow:

Security Logs → KQL Detection → Investigation → IOC Identification → MITRE ATT&CK Mapping → ServiceNow Incident Response

## Attack Scenario

A user account, `john.smith`, showed multiple failed authentication attempts followed by a successful login from an external IP address.

Further investigation identified:

- Repeated failed authentication attempts
- Suspicious PowerShell execution
- Privilege escalation
- Outbound communication with the suspicious IP
- Potential account and endpoint compromise

## Technologies Used

- KQL
- Microsoft Azure
- ServiceNow
- MITRE ATT&CK
- Git / GitHub

## Repository Structure

```text
KQL-ServiceNow-SOC-Lab/
├── Data/
├── Kql/
├── Investigation/
└── Servicenow/