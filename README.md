# Windows Log Analysis & Incident Investigation

## Overview

This project focuses on analyzing Windows security and authentication events to investigate suspicious activity, correlate relevant events, establish an incident timeline, and document security findings.

The investigation covers failed and successful Windows logons and Remote Desktop authentication activity, using event timestamps, account information, and source network information to build an evidence-based investigation.

## Objectives

* Analyze Windows Security Event Logs
* Investigate failed authentication activity
* Investigate successful authentication activity
* Analyze Remote Desktop authentication
* Correlate related security events
* Establish an incident timeline
* Document investigation findings
* Recommend appropriate response actions

---

## Tools & Technologies
* Windows Event Viewer
* Windows Security Event Logs
* Windows Remote Desktop event logs
* Windows authentication event analysis
* Event ID filtering and correlation

---

## Investigation Workflow

```
Windows Event Logs
        ↓
Event Filtering
        ↓
Authentication Analysis
        ↓
Failed Logon Investigation
        ↓
Successful Logon Investigation
        ↓
RDP Authentication Analysis
        ↓
Event Correlation
        ↓
Incident Timeline
        ↓
Investigation Findings
        ↓
Response Recommendations
```
---

## Event IDs Investigated

| Event ID | Activity                      |
| -------- | ----------------------------- |
| 4624     | Successful logon              |
| 4625     | Failed logon                  |
| 1149     | Successful RDP authentication |

## 1. Windows Security Event Analysis

The Windows Security Event Log was analyzed to identify authentication-related activity and relevant security events.
The investigation identified:

* **14 Event ID 4625** failed logon events
* **19 Event ID 4624** successful logon events

The events were filtered and reviewed using timestamps, account information, logon information, and network-related fields.

---

## 2. Failed Authentication Analysis

Event ID `4625` represents a failed Windows logon.

A relevant failed authentication event occurred on:

**`17 May 2025 at 10:53:30 PM`**

Account: `Administrator`

The event was recorded as an authentication failure and was reviewed as part of the authentication investigation.

---

## 3. Successful Authentication Analysis

Event ID `4624` represents a successful Windows logon.

A relevant successful authentication event occurred on:

**`17 May 2025 at 10:53:41 PM`**

Account: `Administrator`

The successful authentication was correlated with surrounding authentication and Remote Desktop activity.

---

## 4. RDP Authentication Analysis

Event ID `1149` was analyzed to investigate Remote Desktop authentication activity.

The relevant event occurred on:

**`17 May 2025 at 10:53:41 PM`**

Details:

**User:** `Administrator`
**Event ID:** `1149`
**Source Network Address:** `10.10.53.248`

The event indicates successful authentication to Remote Desktop Services.

---

## 5. Event Correlation

The relevant events were correlated using timestamps, account information, and event types.

```
10:53:30 PM
4625 — Failed authentication
        ↓
10:53:41 PM
4624 — Successful authentication
        ↓
10:53:41 PM
1149 — Successful RDP authentication
```

The short time interval between these events makes them relevant for further investigation.

The events are not treated individually as proof of malicious activity. Additional context is required to determine whether the authentication activity was expected or unauthorized.

---

## 6. Investigation Findings

The investigation demonstrated the ability to:

* Identify failed authentication attempts
* Identify successful authentication
* Analyze Remote Desktop authentication
* Correlate events using timestamps
* Identify accounts involved in authentication activity
* Review source network information
* Construct an incident timeline
* Document evidence-based findings

---

## 7. Recommended Response Actions

For a production investigation:

**1.** Verify whether the `Administrator` account was expected to authenticate.

**2.** Investigate the source address `10.10.53.248`.

**3.** Review the associated logon type and authentication method.

**4.** Search for additional failed authentication attempts from the same source.

**5.** Search for other successful logons involving the same account.

**6.** Review system and process activity surrounding the authentication.

**7.** Investigate additional Remote Desktop activity.

**8.** Correlate the findings with other available security telemetry.

**9.** Follow established incident-response procedures if unauthorized activity is confirmed.

---

## Skills Demonstrated

* Windows Event Log Analysis
* Windows Security Log Investigation
* Authentication Monitoring
* Event ID Analysis
* Failed Logon Investigation
* Successful Logon Investigation
* RDP Authentication Analysis
* Event Correlation
* Incident Timeline Construction
* Security Investigation
* Incident Response

---

## Evidence

01 — ![Failed Logons (4625)](<img width="1917" height="867" alt="01_failed_logons_4625" src="https://github.com/user-attachments/assets/b6aafdb5-3ad1-4a1a-9d3b-e2b7d02d560c" />)

02 — ![Successful Logon (4624)](<img width="1917" height="867" alt="02_successful_logon_4624" src="https://github.com/user-attachments/assets/e1e6821f-5712-4292-a12b-9fccd58df0c1" />)

03 — ![RDP Authentication (1149)](<img width="1917" height="876" alt="03_rdp_authentication_1149" src="https://github.com/user-attachments/assets/9b27f968-b96f-4ec7-8706-3e2b0074a8c1" />)

04 — ![Windows Security Dataset](<img width="1512" height="688" alt="05_windows_security_100k_events" src="https://github.com/user-attachments/assets/56aaf938-9c18-4bda-b6b7-01c98d2848b9" />)
