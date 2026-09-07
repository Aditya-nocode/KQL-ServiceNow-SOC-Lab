# Security Incident Report

## Incident Title

Suspected Compromise of john.smith

## Severity

High

## Verdict

True Positive - Suspected account compromise with post-compromise activity.

## Summary

Multiple failed login attempts were observed against the account
john.smith from external IP address 185.220.101.47 in the Netherlands.

A successful login subsequently occurred from the same IP address.

Shortly after authentication, suspicious PowerShell activity was observed
on HR-PC-01. The PowerShell command used hidden-window and encoded-command
options.

The account was subsequently added to the local administrators group,
followed by an outbound connection from the internal host to the same
external IP address.

The sequence is consistent with a possible compromised account followed
by execution, privilege escalation, and external communication.

## Evidence

### 1. Authentication Activity

- 8 failed login attempts
- Account: john.smith
- Source IP: 185.220.101.47
- Location: Netherlands
- Time window: approximately 18:24–18:28

### 2. Successful Authentication

- Account: john.smith
- Source IP: 185.220.101.47
- Location: Netherlands
- Time: approximately 18:29

### 3. PowerShell Execution

- Host: HR-PC-01
- Process: powershell.exe
- Observed options: -nop -w hidden -enc
- Time: approximately 18:30

### 4. Privilege Escalation

Command observed:

net localgroup administrators john.smith /add

This added john.smith to the local administrators group.

### 5. Network Activity

- Internal source: 10.10.1.15
- Destination: 185.220.101.47
- Host: HR-PC-01
- Time: approximately 18:37
- Description: Outbound connection to suspicious external IP

## Impact Assessment

Potential impact includes:

- Compromise of the john.smith account
- Unauthorized administrative privileges on HR-PC-01
- Execution of potentially malicious commands
- Possible communication with an external system

No assumption is made that data was successfully exfiltrated because
the available evidence does not directly prove data theft.

## Recommended Actions

1. Disable or temporarily lock the affected account.
2. Reset john.smith credentials.
3. Revoke active sessions/tokens where applicable.
4. Remove unauthorized local administrator membership.
5. Isolate HR-PC-01 for further investigation.
6. Investigate 185.220.101.47 across other systems and accounts.
7. Review PowerShell execution and endpoint telemetry.
8. Check for persistence mechanisms.
9. Review network traffic associated with the external IP.
10. Preserve relevant logs and forensic evidence.

## Detection Method

The incident was identified through KQL analysis of security logs.

Primary investigation techniques:

- Failed login analysis
- Authentication correlation
- Process execution analysis
- Privilege-change analysis
- Network connection analysis

## ServiceNow Incident

The investigation findings were documented and escalated into ServiceNow as a Security Incident.

- Security Incident: SIR0010001
- Affected user: John Smith
- Configuration item: HR-PC-01
- Source: SIEM
- Category: Privilege Escalation
- Incident state: Analysis
- Risk score: 42
- Business impact: 2 - High
- Priority: 3 - Moderate

The incident was progressed through the ServiceNow security incident lifecycle from Analysis to Contain and subsequent response stages. The incident was then closed after documenting the investigation and response.