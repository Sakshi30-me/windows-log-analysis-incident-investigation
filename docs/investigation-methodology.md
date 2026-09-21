# Investigation Methodology

## Objective

The objective of this investigation was to analyze Windows security and authentication events, identify relevant activity, correlate related events, establish an incident timeline, and document investigation findings.

## Investigation Process

The investigation followed a structured Windows log-analysis workflow:

1. Review Windows Security Event Logs.
2. Filter authentication-related Event IDs.
3. Analyze failed authentication activity using Event ID `4625`.
4. Analyze successful authentication activity using Event ID `4624`.
5. Investigate Remote Desktop authentication using Event ID `1149`.
6. Compare event timestamps and account information.
7. Correlate related authentication events.
8. Construct an incident timeline.
9. Document investigation findings.
10. Develop response recommendations.

## Event IDs Analyzed

| Event ID | Activity |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 1149 | Successful RDP authentication |

## Key Fields Reviewed

The investigation reviewed relevant event information including:

- Date and time
- Account name
- Event ID
- Logon information
- Source network address
- Authentication details

## Correlation Method

Events were correlated using:

- Timestamp proximity
- Account information
- Event type
- Source network information

The purpose of correlation was to determine whether separate Windows log entries formed a meaningful sequence of authentication activity.

## Investigation Approach

Individual events were not automatically classified as malicious.

Authentication activity was evaluated in context by considering:

- Whether the account was expected to authenticate
- Whether the source address was expected
- Whether repeated authentication failures occurred
- Whether successful authentication followed failed attempts
- Whether Remote Desktop authentication occurred
- Whether additional security telemetry should be reviewed

## Outcome

The investigation produced a chronological authentication sequence that can be used to support further security analysis and incident-response decision-making.
