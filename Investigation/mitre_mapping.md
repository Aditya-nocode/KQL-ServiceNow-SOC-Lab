# MITRE ATT&CK Mapping

## Investigation Mapping

| Observed Behavior | MITRE ATT&CK Technique | Technique ID | Evidence | Confidence |
|---|---|---|---|---|
| Repeated failed authentication attempts | Brute Force | T1110 | 8 failed authentication attempts against `john.smith` within approximately 8 minutes | Medium |
| Suspicious PowerShell execution | Command and Scripting Interpreter: PowerShell | T1059.001 | Encoded/suspicious PowerShell execution observed on `HR-PC-01` | High |
| Unauthorized addition to local Administrators group | Account Manipulation | T1098 | `john.smith` was added to the local Administrators group | Medium |
| Outbound connection to suspicious external IP | — | — | `HR-PC-01` communicated with `185.220.101.47` | Medium |

## Reasoning

### Authentication Activity

Multiple failed authentication attempts against the same account followed by a successful authentication from the same external IP are consistent with a potential credential attack. This behavior was mapped to **T1110 – Brute Force** with medium confidence.

### PowerShell Execution

Suspicious/encoded PowerShell execution was observed on `HR-PC-01`. This behavior directly corresponds to **T1059.001 – PowerShell** with high confidence.

### Privilege Escalation

The `john.smith` account was added to the local Administrators group. This represents a significant privilege change and was mapped to **T1098 – Account Manipulation** with medium confidence.

### Network Activity

The endpoint established an outbound connection to `185.220.101.47`. The IP was treated as an indicator of compromise during the investigation. No specific MITRE technique was assigned because the available evidence does not establish the application-layer protocol or exact command-and-control technique.