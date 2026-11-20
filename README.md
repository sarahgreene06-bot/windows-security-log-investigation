# SOC-001: Windows Security Log Investigation

## Project Overview

This project demonstrates a beginner-level Security Operations Center (SOC) investigation using Windows Event Viewer.

I investigated Windows authentication logs to identify failed and successful login attempts, examine security events, and determine whether the activity indicated suspicious behavior.

The investigation was performed in an authorized, controlled lab environment on my Windows computer.

## Objective

- Identify failed and successful Windows login attempts.
- Understand Windows Security Event IDs 4624 and 4625.
- Analyze timestamps, logon types, and source network addresses.
- Investigate whether failed authentication attempts were followed by successful authentication.
- Document findings in a security incident report.

## Tools Used

- Windows 11
- Windows Event Viewer
- Windows Security Logs
- GitHub for documentation

## Investigation Process

### Step 1: Access Windows Security Logs

Opened Event Viewer and navigated to:

`Event Viewer > Windows Logs > Security`

Filtered the security logs to examine authentication events.

### Step 2: Identify Failed Login Attempts

Filtered for Event ID 4625.

Two failed authentication events were identified on November 19, 2026:

- 8:49:09 AM — Failed login
- 8:49:14 AM — Failed login

Both events were recorded with Logon Type 2, representing interactive logon attempts.

### Step 3: Investigate Successful Authentication

Filtered for Event ID 4624.

A successful authentication event was identified at 8:49:22 AM.

The event contained:

- Event ID: 4624
- Logon Type: 11 (Cached Interactive)
- Source Network Address: 127.0.0.1 (Loopback)

### Step 4: Analyze the Evidence

The successful authentication occurred eight seconds after the second failed login.

Although the events occurred close together, the available evidence did not conclusively establish that they belonged to the same authentication sequence.

The investigation highlighted the importance of comparing account identifiers, timestamps, logon types, and source information before determining whether suspicious activity represents a security incident.

## Findings

- Two failed authentication events were identified.
- A successful authentication event occurred shortly afterward.
- The events were consistent with the authorized security simulation.
- No unauthorized account access was confirmed.
- Additional correlation would be required before concluding that the events represented a compromised account.

## Evidence

Five redacted screenshots were collected during the investigation and stored in the `screenshots` folder.

The screenshots document Windows authentication events and their associated security details.

## Incident Report

See [SOC-001 Incident Report](incident-report.md) for the full investigation, findings, and recommendations.

## Skills Demonstrated

- Windows Security log analysis
- Authentication event investigation
- Event ID identification
- Basic security event correlation
- Evidence collection
- Incident documentation
- Analytical reasoning

## Lessons Learned

This project taught me that failed login attempts do not automatically indicate a cyberattack.

Security analysts must examine the available evidence, compare related events, and distinguish suspicious activity from confirmed unauthorized access.

I also learned how Windows records different authentication types and how Event Viewer can support security investigations.

## Project Status

Completed introductory Windows authentication investigation.

**Next Learning Goal:** Investigate more complex authentication patterns using unfamiliar security logs and develop stronger event-correlation skills.
