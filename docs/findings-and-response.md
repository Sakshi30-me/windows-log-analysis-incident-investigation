# Findings and Response

## Investigation Findings

The investigation identified a sequence of Windows authentication activity involving the `Administrator` account.

The relevant events were:

- Event ID `4625` — failed authentication
- Event ID `4624` — successful authentication
- Event ID `1149` — successful RDP authentication

The failed authentication occurred at **10:53:30 PM on 17 May 2025**.

A successful Windows logon occurred approximately 11 seconds later at **10:53:41 PM**.

At the same timestamp, a successful RDP authentication event was recorded from:

`10.10.53.248`

## Key Findings

### 1. Failed Authentication

A failed authentication attempt involving the `Administrator` account was identified through Event ID `4625`.

### 2. Successful Authentication

A successful authentication involving the same account was recorded shortly afterward through Event ID `4624`.

### 3. RDP Authentication

Event ID `1149` recorded successful Remote Desktop authentication involving the `Administrator` account and source address `10.10.53.248`.

### 4. Event Correlation

The close timing between the failed authentication, successful authentication, and RDP authentication makes the sequence relevant for further investigation.

The evidence does not independently establish that the activity was malicious. Additional context is required before determining whether the authentication was authorized or unauthorized.

## Recommended Response Actions

If the activity were identified in a production environment, the following actions would be appropriate:

1. Verify whether the `Administrator` account was expected to authenticate.
2. Investigate the source address `10.10.53.248`.
3. Review the associated logon type and authentication method.
4. Search for additional failed logons from the same source.
5. Search for additional successful logons involving the same account.
6. Review Remote Desktop activity around the same time.
7. Examine related system and process activity.
8. Correlate the findings with other available security telemetry.
9. Preserve relevant event logs for continued investigation.
10. If unauthorized activity is confirmed, follow established incident-response procedures.

## Investigation Outcome

The investigation demonstrated a structured approach to Windows log analysis by moving from individual authentication events to event correlation, timeline construction, findings, and response recommendations.

This workflow can be applied to future Windows security investigations involving authentication and Remote Desktop activity.
