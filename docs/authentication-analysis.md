# Authentication Analysis

## Objective

The authentication analysis focused on identifying failed and successful Windows logon activity and examining the relationship between authentication events.

## Event ID 4625 — Failed Logon

Windows Event ID `4625` represents a failed logon attempt.

The investigation identified **14 Event ID 4625 events** in the filtered authentication data.

A relevant event occurred on:

**17 May 2025 at 10:53:30 PM**

Account:

`Administrator`

The failed authentication event was reviewed together with surrounding authentication activity to determine whether a successful authentication followed the failure.

## Event ID 4624 — Successful Logon

Windows Event ID `4624` represents a successful logon.

The investigation identified **19 Event ID 4624 events** in the filtered authentication data.

A relevant event occurred on:

**17 May 2025 at 10:53:41 PM**

Account:

`Administrator`

The successful authentication occurred shortly after the identified failed authentication event.

## Event ID 1149 — RDP Authentication

Windows Event ID `1149` was analyzed to identify successful Remote Desktop authentication activity.

The relevant event occurred on:

**17 May 2025 at 10:53:41 PM**

Details:

- **User:** `Administrator`
- **Source Network Address:** `10.10.53.248`
- **Event ID:** `1149`

The event indicates successful authentication to Remote Desktop Services.

## Authentication Correlation

The relevant events form the following sequence:

| Time | Event ID | Activity |
|---|---:|---|
| 10:53:30 PM | 4625 | Failed authentication |
| 10:53:41 PM | 4624 | Successful authentication |
| 10:53:41 PM | 1149 | Successful RDP authentication |

The successful authentication and RDP authentication occurred shortly after the failed authentication event.

This sequence was treated as security-relevant activity requiring contextual investigation rather than as automatic proof of unauthorized access.

## Investigation Considerations

Further investigation should consider:

- Whether the `Administrator` account was expected to authenticate.
- Whether `10.10.53.248` was an authorized source.
- The logon type associated with the authentication.
- Additional failed logons from the same source.
- Additional successful logons involving the same account.
- Other Remote Desktop activity around the same time.
- Related system and process activity.

## Conclusion

The authentication analysis demonstrated how failed logons, successful logons, and RDP authentication events can be examined together to identify potentially relevant activity and establish an investigation timeline.
