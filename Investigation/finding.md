# Investigation Findings

## Summary

The investigation identified suspicious activity involving the account `john.smith` and endpoint `HR-PC-01`.

## Key Findings

- 8 failed authentication attempts were observed within approximately 8 minutes.
- The authentication activity originated from `185.220.101.47` (Netherlands).
- A successful authentication was subsequently observed.
- Suspicious/encoded PowerShell execution was identified on `HR-PC-01`.
- The account was added to the local Administrators group.
- `HR-PC-01` subsequently established an outbound connection to `185.220.101.47`.

## Assessment

The combined evidence is consistent with a potential account compromise followed by privilege escalation and suspicious outbound communication.

## Indicators of Compromise

| Indicator | Value |
|---|---|
| User | `john.smith` |
| Host | `HR-PC-01` |
| IP Address | `185.220.101.47` |
| Location | Netherlands |
| Activity | Authentication, PowerShell, privilege escalation, network communication |