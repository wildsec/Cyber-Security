# MITRE ATT&CK

The MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) framework is a comprehensive global knowledge repository that meticulously documents the tactics and techniques employed by threat actors at every stage of a cyber-attack. It functions as a strategic playbook, providing detailed insights into attackers' methods, from **gaining initial access** to **maintaining a presence**, **escalating privileges**, **evading defenses**, **moving laterally within a network**, and much more.

## Format

|Format|Sample|Explanation|
|---|---|---|
|**ATT&CK Tactic**::**ATT&CK Technique**::**Technique Identifier**|Defense Evasion::Obfuscated Files or Information::T1027|**DEFENSE EVASION =** ATT&CK Tactic<br>**Obfuscated Files or Information =** ATT&CK Technique<br>**T1027 =** Technique Identifier|
|**ATT&CK Tactic**::**ATT&CK Technique**::**ATT&CK Sub-Technique**::**Technique Identifier**[.]Sub-technique **Identifier**|Defense Evasion::Obfuscated Files or Information::Indicator Removal from Tools T1027.005|**DEFENSE EVASION** = ATT&CK Tactic<br>**Obfuscated Files or Information** = ATT&CK Technique<br>**Indicator Removal from Tools** = ATT&CK Sub-Technique<br>**T1027 =** Technique Identifier<br>**005** = Sub-Technique Identifier|

## Matrix

The [MITRE ATT&CK Matrix](https://attack.mitre.org/matrices/) is a powerful visual representation of all tactics and techniques that exist within the framework. You can also utilize the [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/), a handy tool for annotating and exploring matrices. The tactics are represented across the top of the matrix. Each tactic contains techniques nested below, which can be expanded to reveal sub-techniques.

1. **Tactic**: Let's say that an attacker wants to perform Reconnaissance on their target. This is the attacker's goal.
2. **Technique**: They may utilize the Active Scanning technique. This is how they achieve their Reconnaissance goal.
3. **Sub-technique**: Active Scanning comprises three specific methods: Scanning IP Blocks, Vulnerability Scanning, or Wordlist Scanning.

## Who Uses ATT&CK?

|Who|Their Goal|How They Use ATT&CK|
|---|---|---|
|Cyber Threat Intelligence (CTI) Teams|Collect and analyze threat information to improve an organization's security posture|Map observed threat actor behavior to ATT&CK TTPs to create profiles that are actionable across the industry|
|SOC Analysts|Investigate and triage security alerts|Link activity to tactics and techniques to provide detailed context for alerts and prioritize incidents|
|Detection Engineers|Design and improve detection systems|Map SIEM/EDR and other rules to ATT&CK to ensure better detection efforts|
|Incident Responders|Respond to and investigate security incidents|Map incident timelines to MITRE tactics and techniques to better visualize the attack.|
|Red & Purple Teams|Emulate adversary behavior to test and improve defenses|Build emulation plans and exercises aligned with techniques and known group operations|

## Related Frameworks
- [D3FEND](D3FEND.md) - MITRE's detection and defense framework
- [CAR](CAR.md) - Cyber Analytics Repository
- [Unified Kill Chain](../Unified%20Kill%20Chain.md) - Alternative attack framework
- [Cyber Kill Chain](../Cyber%20Kill%20Chain.md) - Lockheed Martin's framework
