# Incident Response

## Type of Incidents
* Malware Infections
* Security Breaches
* Data Leaks
* Insider Attacks
* Denial of Service Attacks
* ...

## SANS Framework

| Phase | Explanation | Example |
|-------|-------------|---------|
| Preparation | This is the first phase. The preparation phase includes building the necessary resources to handle an incident. These resources include developing incident response teams, having a proper incident response plan in place, and deploying necessary security solutions to combat the incidents. | Conducting awareness training for employees on phishing emails. Phishing emails are fraudulent emails sent by malicious attackers that can trick you into performing actions that can lead you to an incident. |
| Identification | The identification phase refers to looking for any abnormal behavior that may indicate an incident. This involves using various security solutions and techniques to monitor abnormal events. | The security team notices a huge amount of data being sent out from one of the hosts. Upon analysis, it was found to be compromised after a malicious file was downloaded from a phishing email attachment. |
| Containment | Once an incident has been identified, the next step should be to contain it. This means minimizing the impact of the attack. This is usually done by isolating the victim machine, disabling the compromised user accounts, etc. | The Security team isolates the host from the network to minimize the impact and not allow the attacker to jump to other systems, leveraging the compromised host. |
| Eradication | This phase, as its name suggests, involves removing the threat from the attacked environment. The threat may be of any kind. The eradication phase will ensure the subject environment is clean, and now we can move to the recovery phase. | A deep malware scan was executed on the system to remove the malicious software from the host. |
| Recovery | The recovery phase is very important in this chain. It involves recovering the affected systems from backup or rebuilding them. The recovered systems are then tested and are ready to use. | The compromised host was re-configured, and the exfiltrated data was restored from the backup. |
| Lessons Learned | This is also an important part of the incident response lifecycle. Gaps in the detection and analysis of the incident are identified and documented, helping to improve the overall process in future incidents. | Conducting a post-incident review meeting to analyze the incident's root cause and improve the security to prevent future attacks. |

## NIST Framework
Preparation -> Detection and Analysis -> Containment, Eradication and Recovery -> Post-Incident Activity

## Incident Response Plan
- Roles and Responsibilities
- Incident Response methodology
- Communication plan with stakeholders, including law enforcement
- Escalation path to be followed

## Technology
- **SIEM:** [General](Defensive/SIEM/General.md) - The Security Information and Event Management Solution collects all important logs in one centralized location and correlates them to identify incidents.
- **AV:** Antivirus detects known malicious programs in a system and regularly scans your system for these.
- **EDR:** [EDR](EDR.md) - Endpoint Detection and Response is deployed on every system, protecting it against some advanced-level threats. This solution can also contain and eradicate the threat.

## Playbooks
Playbooks are the guidelines for a comprehensive incident response.

Following is an example of a **Playbook** for an incident: Phishing Email
1. Notify all the stakeholders of the phishing email incident
2. Determine if the email was malicious by conducting header and body analysis of the email
3. Look for any attachments with the email and analyze them
4. Determine if anybody opened the attachments
5. Isolate the infected systems from the network
6. Block the email sender

## Runbooks
**Runbooks**, on the other hand, are the detailed, step-by-step execution of specific steps during different incidents. These steps may vary depending on the resources available for investigation.

## Related Topics
- [SOC](SOC/General.md) - Security Operations Center
- [Blue Team](Blue%20Team.md) - Defensive security team
- [Phishing](../Email/Phishing/Email%20Phishing%20Characteristics.md) - Phishing email characteristics
