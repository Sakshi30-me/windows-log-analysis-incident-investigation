# Incident Timeline

## Timeline Objective

The purpose of the timeline is to organize related Windows authentication events chronologically and identify the sequence of activity surrounding the authentication investigation.

## Authentication Timeline

| Date | Time | Event ID | Activity | Account | Source |
|---|---|---:|---|---|---|
| 17 May 2025 | 10:53:30 PM | 4625 | Failed logon | Administrator | Windows authentication logs |
| 17 May 2025 | 10:53:41 PM | 4624 | Successful logon | Administrator | Windows authentication logs |
| 17 May 2025 | 10:53:41 PM | 1149 | Successful RDP authentication | Administrator | `10.10.53.248` |

## Event Sequence

```text
10:53:30 PM
4625 — Failed Logon
        │
        │ 11 seconds
        ↓
10:53:41 PM
4624 — Successful Logon
        │
        │ Same timestamp
        ↓
10:53:41 PM
1149 — Successful RDP Authentication
        │
        ↓
Source: 10.10.53.248
Account: Administrator
```

## Timeline Analysis

The first relevant event was a failed authentication attempt involving the `Administrator` account.

Approximately 11 seconds later, a successful Windows logon involving the same account was recorded.

At the same timestamp as the successful logon, Event ID `1149` recorded successful Remote Desktop authentication involving the `Administrator` account and source address `10.10.53.248`.

The close temporal relationship between these events makes the sequence relevant for further investigation.

## Investigation Context

The timeline establishes a sequence of authentication-related activity but does not independently establish that the activity was malicious.

Additional investigation should determine:

Whether the `Administrator` account was expected to authenticate.
Whether the source address was authorized.
Whether the RDP connection was expected.
Whether additional failed or successful authentication events occurred.
Whether related process or system activity followed the authentication.

## Timeline Conclusion

The correlated events provide a chronological representation of authentication activity and establish a starting point for further incident investigation and response.
