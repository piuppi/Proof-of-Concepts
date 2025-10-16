# CVE-2025-57521

### Description
Bambu Studio 2.1.1.52 and earlier is affected by a vulnerability that allows arbitrary code execution during application startup. The application loads a network plugin without validating its digital signature or verifying its authenticity. A local attacker can exploit this behavior by placing a malicious component in the expected location, which is controllable by the attacker (e.g., under %APPDATA%), resulting in code execution within the context of the user. The main application is digitally signed, which may allow a malicious component to inherit trust and evade detection by security solutions that rely on signed parent processes.

### Overview
Bambu Lab (https://bambulab.com) is a consumer tech company focusing on desktop 3D printers. Starting with the X1 series, BambuLab builds state-of-the-art 3D printers that break the barriers between the digital and physical worlds, bringing creativity to a whole new level. Bambu Lab has three sites, located in Shenzhen and Shanghai, China, and Austin, Texas, U.S.

### Impact
The following impacts describe realistic risks and attacker capabilities that can arise from this vulnerability. These are written to help defenders and risk owners prioritise mitigation.

**Arbitrary code execution in user context**: an attacker controlling a writable plugin/location can cause arbitrary code to run when the application starts. Execution runs with the privileges of the user that launches Bambu Studio.

**Persistence**: by placing a component in a location that Bambu Studio loads automatically on startup, an attacker can achieve persistence on the affected host (the malicious component will be executed every time the user runs the application).

**Defense evasion via parent-process trust**: because the main Bambu Studio process is digitally signed, security products and detection logic that trust or whitelist signed parent processes may be bypassed. A malicious plugin loaded by the signed process can inherit the parent's reputation for the purposes of some heuristics and allow further malicious activity to proceed with reduced scrutiny.

### Timeline
- **2024-10-12**: Discovered and reported to [BambuLab Security Team](https://bambulab.com/en-us/security)
- **2025-01-28**: Got response from BambuLab Security Team, "*Thank you for contacting BambuLab Security. We apologize for the delay due to our bug bounty program being in its trial phase. we are working to improve our response times....{SNIP}*"
- **2025-06-26**: After several attempts to follow up, I never received a response from the BambuLab Security team, so I decided to open an issue on their GitHub repository, hoping to get a reply from the development team.
- **2025-06-28**: The BambuLab development team, in coordination with their security team, acknowledged the vulnerability while responding on the GitHub issue, and confirmed that a fix was scheduled to be included within the next two product releases.
- **2025-10-16**: The BambuLab develompent team introduced the vulnerability fix in version 2.3.0.70 of the product and asked me to test its effectiveness.
- **2025-10-16**: MITRE has assigned [CVE-2025-57521](https://nvd.nist.gov/vuln/detail/CVE-2025-57521) to this vulnerability, and I have published a proof of concept (PoC).

### Discovered by

#### [Gianluca Palma](https://www.linkedin.com/in/piuppi/) ([@piuppi](https://twitter.com/piuppi)) of [Engineering Ingegneria Informatica S.p.A.](https://www.eng.it)

### References

- **GitHub Issue #7405**  
  <https://github.com/bambulab/BambuStudio/issues/7405>  
- **BambuLab BugFix Release Notes**  
  <https://wiki.bambulab.com/en/software/bambu-studio/release/release-note-2-3-0>  
- **GitHub Commit Fixing the Vulnerability**
  <https://github.com/bambulab/BambuStudio/commit/969763122f06e649350033eea95fbfe08d85bbbd>

### Proof of concept (POC)

A short demonstration video (PoC_CVE-2025-57521.mp4) is attached as a release asset. The recording shows the conditions and observable result, it is intended for review by vendors, CERTs and defenders.

[Watch the PoC video](videos/PoC_CVE-2025-57521.mp4)

### Remediation Recommendations

- If your software loads components that interact with the network, always verify their digital signature before loading them.
- Pay special attention to components stored in locations that could potentially be controlled by an attacker.
- Consider restricting write permissions to directories from which network-interacting components are loaded.
- Regularly review and update all third-party components to ensure they come from trusted sources.
