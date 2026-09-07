# Security Incident Timeline

## Incident: Suspected Compromise of john.smith

| Time | Event | Source | Significance |
|---|---|---|---|
| 18:24 | Failed login | 185.220.101.47 (Netherlands) | Initial authentication attempts |
| 18:25 | Failed login | 185.220.101.47 (Netherlands) | Repeated authentication failure |
| 18:26 | Failed login | 185.220.101.47 (Netherlands) | Repeated authentication failure |
| 18:27 | Failed login | 185.220.101.47 (Netherlands) | Repeated authentication failure |
| 18:28 | Failed login | 185.220.101.47 (Netherlands) | Repeated authentication failure |
| 18:29 | Successful login | 185.220.101.47 (Netherlands) | Authentication succeeded after repeated failures |
| 18:30 | Suspicious PowerShell execution | HR-PC-01 | Hidden and encoded PowerShell |
| 18:34 | Privilege escalation | HR-PC-01 | john.smith added to local administrators |
| 18:37 | Outbound network connection | HR-PC-01 → 185.220.101.47 | Suspicious external connection |

## Attack Chain

Repeated failed authentication
→ Successful authentication
→ Suspicious PowerShell execution
→ Privilege escalation
→ Outbound connection