# MuseHub - Local Privilege Escalation to SYSTEM

- **Severity:** High
- **CVSS v3.1:** 7.8 - `CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H`
- **Weaknesses:** CWE-732 (Incorrect Permission Assignment for Critical Resource), CWE-269 (Improper Privilege Management), CWE-426 (Untrusted Search Path)
- **Vendor:** Muse Group - MuseHub (Windows)
- **Affected component:** `MuseHubUpdaterService` (Windows service, runs as `NT AUTHORITY\SYSTEM`)
- **Affected version confirmed by testing:** MuseHub for Windows `2.9.3 (2300)`
- **Fixed version:** MuseHub for Windows `3.4.0 (2335)`
- **Reporter:** [Gianluca Palma (piuppi)](https://www.linkedin.com/in/piuppi) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)

## Summary

MuseHub for Windows versions prior to 3.4.0 (2335) contain a local privilege escalation vulnerability in MuseHubUpdaterService. The service runs as NT AUTHORITY\SYSTEM and exposes an unauthenticated named pipe, `\\.\pipe\Muse.Updater.Pipe`, that grants read and write access to local users. The `UpdateMuseHub` request handler accepts a caller-controlled executable path, validates only the executable's Muse Group Authenticode signature, and launches it with SYSTEM privileges. A local attacker can copy a validly signed executable to a user-writable directory, place a malicious DLL alongside it, and invoke the handler through the named pipe. Due to DLL search order behavior, the executable loads the attacker-controlled DLL, allowing arbitrary code execution as NT AUTHORITY\SYSTEM and local privilege escalation.

## Impact

A local, low-privileged user can escalate privileges to **`NT AUTHORITY\SYSTEM`** and execute arbitrary code with the highest local privilege level.

## Affected versions

- **Product:** MuseHub (Muse Group) for Windows
- **Component:** `MuseHubUpdaterService`
- **Version confirmed vulnerable by testing:** `2.9.3 (2300)`
- **Fixed version:** `3.4.0 (2335)`

## Remediation

Update MuseHub for Windows to version `3.4.0 (2335)` or later.


## Timeline

| Date | Activity |
|------|----------|
| 15/09/2026 | Responsible disclosure initiated via a MuseHub support request |
| 17/09/2026 | MuseHub support replied and confirmed that communication could continue through that channel |
| 17/09/2026 | CVE ID reservation requested from MITRE |
| 18/09/2026 | Report and proof of concept sent to the MuseHub team |
| 24/09/2026 | Vulnerability acknowledged by the vendor |
| 28/09/2026 | Fix implemented by the MuseHub team |
| 29/09/2026 | Fix confirmed using the release-candidate build provided by the MuseHub team |
| 29/09/2026 | Public release of MuseHub `3.4.0 (2335)`, fixing the vulnerability and crediting the reporter |
| 19/10/2026 | Public advisory published in coordination with the MuseHub support team |

## Credit

Reported by **[Gianluca Palma (piuppi)](https://www.linkedin.com/in/piuppi) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)**.

## References

- **Vendor changelog:** https://support.musehub.com/en/articles/17327414-windows-changelog#h_7d60fe0a42
- **CVE record:** To be added once the CVE ID is assigned and the record is published.
