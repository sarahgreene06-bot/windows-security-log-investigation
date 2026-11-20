# SOC-001 — Incident Report

**Date:** November 19–20, 2026  
**Environment:** Personal Windows 11 workstation  
**Tool:** Windows Event Viewer  
**Classification:** Authorized simulation  
**Confirmed compromise:** No

## Objective
Determine whether intentionally generated failed Windows logon events could be detected, examined and correlated with nearby successful logons.

## Evidence
- 08:49:09 — 4625 — Failed interactive logon (Type 2)
- 08:49:14 — 4625 — Failed interactive logon (Type 2)
- 08:49:22 — 4624 — Successful cached interactive logon (Type 11)
- Loopback source address: `127.0.0.1`
- Failure status: `0xC000006D`; substatus: `0xC0000380`
- Process observed: `C:\Windows\System32\svchost.exe`

## Analysis
Two failed logon events were recorded five seconds apart during a controlled test. A successful cached interactive logon followed eight seconds later. The failed records did not identify the target account, and the successful event used a different logon type. These limitations prevent definitive event-to-session correlation based on the captured evidence alone.

## Assessment and response
The activity is consistent with authorized testing. No evidence reviewed confirms unauthorized access. No containment was necessary for this known simulation.

## Recommendations
Maintain security auditing, investigate unexplained failure bursts, verify account and source details, and avoid declaring compromise based solely on close timestamps.

## Lessons learned
Security analysts must distinguish observed facts, reasonable interpretations, and unverified assumptions.
