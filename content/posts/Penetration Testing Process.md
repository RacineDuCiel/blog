---
title: 'Penetration Testing Process'
date: 2024-04-22
tags: ["security"]
TocOpen: true
---


## Pentest overview 

**Risk Management**

- **Objective**: Identify, evaluate, and mitigate risks threatening confidentiality, integrity, and availability of information systems.
- **Strategies**: Accept, transfer, avoid, or mitigate risks to maintain an acceptable risk level.
- **Inherent Risk**: Persistent risk despite implemented security controls, necessitating ongoing risk management efforts.


**Vulnerability Assessments**

- **Automated Tools**: Utilize scanning tools like Nessus, Qualys, OpenVAS for systematic identification of known vulnerabilities.
- **Manual Testing**: Essential for adapting attacks to target system configurations and uncovering nuanced vulnerabilities.
- **Authorization**: Imperative for legal and ethical testing; explicit written authorization required to avoid legal repercussions.

**Testing Methods**

- **External**: Assess network perimeter from outside, evaluating defenses against external threats.
- **Internal**: Test from within the corporate network, simulating insider threats or assuming a breached scenario.

| **Type**         | **Information Provided**                                                                                                                                                                                                                                              |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Blackbox`       | `Minimal`. Only the essential information, such as IP addresses and domains, is provided.                                                                                                                                                                             |
| `Greybox`        | `Extended`. In this case, we are provided with additional information, such as specific URLs, hostnames, subnets, and similar.                                                                                                                                        |
| `Whitebox`       | `Maximum`. Here everything is disclosed to us. This gives us an internal view of the entire structure, which allows us to prepare an attack using internal information. We may be given detailed configurations, admin credentials, web application source code, etc. |
| `Red-Teaming`    | May include physical testing and social engineering, among other things. Can be combined with any of the above types.                                                                                                                                                 |
| `Purple-Teaming` | It can be combined with any of the above types. However, it focuses on working closely with the defenders.                                                                                                                                                            |

**Types of Testing Environments**

- **Diverse Scope**: Covers network, web applications, mobile apps, APIs, thick clients, IoT devices, cloud services, source code, physical security, employees, hosts, servers, security policies, firewalls, IDS/IPS.
- **Comprehensive Coverage**: Ensures holistic assessment of all components potentially vulnerable to attacks.

## Laws and Regulations

**Laws and Regulations:**

*USA:*

1. **Computer Fraud and Abuse Act (CFAA):** Criminalizes unauthorized computer access, including hacking and identity theft.
2. **Digital Millennium Copyright Act (DMCA):** Prohibits circumventing copyright protection measures.
3. **Electronic Communications Privacy Act (ECPA):** Regulates interception of electronic communications.
4. **Health Insurance Portability and Accountability Act (HIPAA):** Governs use and disclosure of protected health information.
5. **Children's Online Privacy Protection Act (COPPA):** Regulates collection of personal information from children under 13.

*Europe:*

1. **General Data Protection Regulation (GDPR):** Regulates handling of personal data and imposes penalties for non-compliance.
2. **Network and Information Systems Directive (NISD):** Requires security measures and incident reporting for essential services.
3. **Cybercrime Convention of the Council of Europe:** Facilitates cooperation between countries in investigating cybercrime.
4. **E-Privacy Directive 2002/58/EC:** Regulates processing of personal data in electronic communication sector.

*UK:*

1. **Computer Misuse Act 1990:** Criminalizes unauthorized computer access and misuse.
2. **Data Protection Act 2018:** Provides legal rights and protections regarding personal data.
3. **Human Rights Act 1998 (HRA):** Protects fundamental rights and freedoms.
4. **Police and Justice Act 2006:** Establishes criminal offenses and measures for crime prevention.
5. **Investigatory Powers Act 2016 (IPA) and Regulation of Investigatory Powers Act 2000 (RIPA):** Regulates investigatory powers and covert techniques.

*India:*

1. **Information Technology Act 2000:** Recognizes electronic transactions and criminalizes hacking.
2. **Personal Data Protection Bill 2019:** A proposed legislation for personal data protection.
3. **Indian Evidence Act of 1872 and Indian Penal Code of 1860:** Relevant provisions for cybercrime cases.

*China:*

1. **Cyber Security Law:** Protects critical information infrastructure and personal data.
2. **National Security Law:** Criminalizes activities threatening national security.
3. **Anti-Terrorism Law:** Criminalizes activities supporting terrorism.
4. **Measures for the Security Assessment of Cross-border Transfer of Personal Information and Important Data:** Regulates cross-border data transfer.
5. **State Council Regulation on the Protection of Critical Information Infrastructure Security:** Regulates critical information infrastructure protection.

---

**Precautionary Measures during Penetration Tests:**

☐ Obtain written consent from the owner or authorized representative.
☐ Conduct testing within the scope of consent and respect limitations.
☐ Take measures to prevent damage to systems or networks being tested.
☐ Do not access, use, or disclose personal data without permission.
☐ Do not intercept electronic communications without consent.
☐ Do not test systems covered by HIPAA without proper authorization.


## Stages of Penetration Testing
 
It is essential to distinguish between `deterministic` and `stochastic` processes. A deterministic process is a process in which each state is causally dependent on and determined by other previous states and events. A stochastic process is one in which one state follows from other states only with a certain probability. Here, only statistical conditions can be assumed. For us, several of the above definitions overlap. We use the definition of the penetration testing process from the social sciences to represent `a course of events connected` with `deterministic processes`. This is because all of our steps are based on the events and results we can discover or provoke.


**Stages :**

1. **Pre-Engagement:**
   - Educate the client and adjust the contract.
   - Define tests and components.
   - Arrange non-disclosure agreements, goals, scope, time estimation, and rules of engagement.

2. **Information Gathering:**
   - Obtain information about target company, software, and hardware.
   - Search for potential security gaps.

3. **Vulnerability Assessment:**
   - Analyze information gathered.
   - Identify known vulnerabilities in systems, applications, and versions.
   - Determine threat level and susceptibility to cyber-attacks.

4. **Exploitation:**
   - Test attacks against potential vectors.
   - Execute attacks to gain initial access to target systems.

5. **Post-Exploitation:**
   - Maintain access to exploited machine.
   - Escalate privileges if possible.
   - Hunt for sensitive data.
   - Demonstrate impact to client.
   
6. **Lateral Movement:**
   - Move within internal network to access additional hosts.
   - Iterate with post-exploitation activities.
   - Use various techniques based on exploited host information.

7. **Proof-of-Concept:**
   - Document steps taken to achieve network compromise.
   - Create clear picture of vulnerabilities for client.
   - Automate steps if feasible.
   
8. **Post-Engagement:**
   - Prepare detailed documentation for administrators and management.
   - Clean up traces of actions on hosts and servers.
   - Create deliverables for client.
   - Archive testing data.
   
## Pre-engagement


1. **Scoping Questionnaire:**
   - Understand client requirements.
   - Identify assessment types: Internal/External Penetration Test, Vulnerability Assessment, Social Engineering, etc.
   - Determine scope: IP ranges, domains, applications, wireless networks, physical locations.
   - Gather specifics: Expected live hosts, domains/subdomains, web/mobile apps, wireless SSIDs, phishing targets.
   - Clarify assessment depth: Black box, grey box, white box.
   - Assess evasiveness: Non-evasive, hybrid-evasive, fully evasive.
   - Review information disclosure preferences.

2. **Pre-Engagement Meeting:**
   - Initiate client discussion.
   - Sign Non-Disclosure Agreement (NDA).
   - Define goals, scope, time estimation, rules of engagement (RoE).
   - Identify client signatory authority.
   - Prepare essential documents: NDA, Scoping Questionnaire, Penetration Testing Proposal, Rules of Engagement.
   - Address urgent cases or exceptions.

|**Type**|**Description**|
|---|---|
|`Unilateral NDA`|This type of NDA obligates only one party to maintain confidentiality and allows the other party to share the information received with third parties.|
|`Bilateral NDA`|In this type, both parties are obligated to keep the resulting and acquired information confidential. This is the most common type of NDA that protects the work of penetration testers.|
|`Multilateral NDA`|Multilateral NDA is a commitment to confidentiality by more than two parties. If we conduct a penetration test for a cooperative network, all parties responsible and involved must sign this document.|


3. **Kick-Off Meeting:**
   - Detailed discussion post-contract signing.
   - Attendees: Client POC(s), technical staff, testing team.
   - Explain penetration testing process.
   - Discuss potential risks and emergency procedures.
   - Outline testing limitations and restrictions.
   - Clarify communication channels and reporting expectations.
   - Review payment terms and schedules.

4. **Contractors Agreement (Physical Tests):**
   - Required for physical testing legality.
   - Include building layout, physical addresses, room identifications, components.
   - Define timeline and notarization requirements.
   - Obtain permission to test.

5. **Setting Up:**
   - Plan and prepare post-information gathering.
   - Setup virtual machines, VPS, and tools.
   - Ensure all systems are ready for various scenarios.
   - Consult Setting Up module for detailed instructions.

**Considerations:**
- Legal compliance crucial: NDAs, permissions, contracts.
- Clear communication is key for successful engagement.
- Adapt approach to each client's unique needs and preferences.
- Regularly update and refine the process based on feedback and evolving requirements.

## Information gathering

1. **Open-Source Intelligence (OSINT):**
   - Process for finding publicly available information.
   - Identify events, dependencies, and connections.
   - Utilize freely available sources.
   - Search for sensitive information on platforms like Github.

2. **Infrastructure Enumeration:**
   - Use OSINT and active scans.
   - Map the company's internet and intranet position.
   - Identify servers, hosts, name servers, mail servers, web servers, etc.
   - Determine security measures and firewall configurations.

3. **Service Enumeration:**
   - Identify network services and versions.
   - Understand service purpose and usage.
   - Check version history for vulnerabilities.
   - Find misconfigurations or outdated services.

4. **Host Enumeration:**
   - Examine each host listed in the scoping document.
   - Determine operating systems, services, and versions.
   - Look for FTP servers, unsupported operating systems, and vulnerabilities.
   - Identify internal services often overlooked for security.

5. **Pillaging (Post-Exploitation):**
   - Collect sensitive information locally on exploited hosts.
   - Gather employee names, customer data, and more.
   - Pillaging is an integral part of information gathering and privilege escalation.
   - Exploit target systems to retrieve valuable data.

6. **Note on Pillaging:**
   - Pillaging is not a standalone stage but part of information gathering and privilege escalation.
   - Covered across various modules, including network enumeration, privilege escalation, and attacking common services.
   - Practice extensively through simulated mini penetration tests and operating system-specific modules.

**Key Considerations:**
- OSINT provides valuable insights into a company's online presence.
- Infrastructure and service enumeration reveal potential attack vectors and vulnerabilities.
- Host enumeration uncovers internal vulnerabilities often overlooked.
- Pillaging is essential for gathering sensitive data post-exploitation.
- Regular practice and exploration across modules enhance proficiency in information gathering techniques.


## Vulnerability Assessment

1. **Analysis Types:**
   - **Descriptive:** Describe data sets based on individual characteristics.
   - **Diagnostic:** Clarify causes, effects, and interactions.
   - **Predictive:** Create predictive models for future probabilities.
   - **Prescriptive:** Determine actions to eliminate or prevent future problems.

2. **Conclusions Formation:**
   - Analyze gathered information to draw conclusions.
   - Ask precise questions and assess known and unknown factors.
   - Confirm or disprove hypotheses through testing.

3. **Vulnerability Research and Analysis:**
   - Part of descriptive analysis.
   - Identify network or system components.
   - Search for known vulnerabilities and exploits.
   - Utilize sources like CVEdetails, Exploit DB, Vulners, etc.
   - Diagnose vulnerabilities to understand causes.

4. **Assessment of Attack Vectors:**
   - Test services and applications found during research.
   - Combine historical and current information for analysis.
   - Replicate target systems for covert testing if evasion is required.

5. **Iterative Process:**
   - If vulnerabilities aren't detected, return to Information Gathering.
   - Overlapping stages require continuous back and forth movement.
   - Quality and intensity are crucial; prioritize thorough analysis over speed.
   - Real penetration tests prioritize quality to prevent successful hacks.

**Key Considerations:**
- Use various analysis types to understand data and draw meaningful conclusions.
- Thoroughly research vulnerabilities using reputable sources.
- Adapt Proof-Of-Concepts and configurations to fit specific cases.
- Test covertly if required and mirror target systems for accurate assessment.
- Prioritize quality and thoroughness in penetration testing to prevent successful hacks.

## Exploitation

1. **Exploitation Stage Overview:**
   - Adapt weaknesses to obtain desired roles (e.g., foothold, escalated privileges).
   - Close connection between phases; maintain clarity in process.

2. **Prioritization of Attacks:**
   - Assess based on:
     - Probability of Success.
     - Complexity.
     - Probability of Damage.
   - Use CVSS Scoring and personal point system for evaluation.
   - Example prioritization:
   
|                           | Remote File Inclusion | Buffer Overflow |
| ------------------------- | --------------------- | --------------- |
| 1. Probability of Success | 10                    | 8               |
| 2. Complexity - Easy      | 5                     | 0               |
| 3. Complexity - Medium    | 3                     | 3               |
| 4. Complexity - Hard      | 1                     | 0               |
| 5. Probability of Damage  | -5                    | -5              |
| total                     | 14                    | 6               |


1. **Preparation for Attack:**
   - Reconstruct exploit locally if necessary.
   - Set up VM to mirror target environment closely.
   - Test exploit on local VM before execution.
   - Check with client if unsure; communicate risks and findings clearly.
   - Exercise caution; prioritize safety and minimize disruptions.

**Key Considerations:**
- Adapt PoCs to establish connections and execute desired actions.
- Prioritize attacks based on success probability, complexity, and potential damage.
- Test exploits locally before execution; communicate with clients for informed decisions.
- Exercise caution and prioritize safety during exploitation; communicate findings clearly.


## Post exploitation


1. **Post-Exploitation Overview:**
   - Stage following successful exploitation.
   - Aims to obtain sensitive and business-relevant information.
   - Components:
     - Evasive Testing
     - Information Gathering
     - Pillaging
     - Vulnerability Assessment
     - Privilege Escalation
     - Persistence
     - Data Exfiltration

2. **Evasive Testing:**
   - Avoids detection by skilled administrators.
   - Divided into three categories: Evasive, Hybrid Evasive, Non-Evasive.
   - Goal: Identify and rectify clients' security blind spots.

3. **Information Gathering:**
   - Reassess system and network from internal perspective.
   - Enumerate local network and services.
   - Explore shares and local services for data gathering (Pillaging).

4. **Pillaging:**
   - Analyze host's role in corporate network.
   - Investigate network configurations and traffic.
   - Hunt for sensitive data like passwords and credentials.

5. **Persistence:**
   - Maintain access to exploited host.
   - Essential for uninterrupted access after initial exploitation.
   - Adapt strategies based on system configurations.

6. **Vulnerability Assessment:**
   - Repeat assessment from inside the system.
   - Prioritize vulnerabilities and plan escalation of privileges.
   - Weigh potential exploits against risks of disrupting services.

7. **Privilege Escalation:**
   - Crucial for accessing higher privileges on system or domain.
   - Obtain root/administrator/SYSTEM privileges for broader network access.
   - Can involve exploiting stored credentials from other users.

8. **Data Exfiltration:**
   - Test possibility of transferring sensitive data from target system to attacker's.
   - Check with client and adhere to data security regulations.
   - Simulate exfiltrating fake data to test protection mechanisms.

**Frameworks and Regulations:**

| **Type of Information**               | **Security Regulation**                                         |
| ------------------------------------- | --------------------------------------------------------------- |
| Credit Card Account Information       | `Payment Card Industry` (`PCI`)                                 |
| Electronic Patient Health Information | `Health Insurance Portability and Accountability Act` (`HIPAA`) |
| Consumers Private Banking Information | `Gramm-Leach-Bliley` (`GLBA`)                                   |
| Government Information                | `Federal Information Security Management Act of 2002` (`FISMA`) |

Some frameworks companies may follow include:

|   |   |
|---|---|
|(`NIST`) - National Institute of Standards and Technology|(`CIS Controls`) - Center for Internet Security Controls|
|(`ISO`) - International Organization for Standardization|(`PCI-DSS`) - The Payment Card Industry Data Security Standard|
|(`GDPR`) - General Data Protection Regulation|(`COBIT`) - Control Objectives for Information and Related Technologies|
|(`FedRAMP`) - The Federal Risk and Authorization Management Program|(`ITAR`) - International Traffic in Arms Regulations|
|(`AICPA`) - American Institute of Certified Public Accountants|(`NERC CIP Standards`) - NERC Critical Infrastructure Protection Standards|

## Lateral movement

1. **Introduction to Lateral Movement:**
   - Follows successful Exploitation and Post-Exploitation stages.
   - Objective: Test attacker's reach within the entire network.
   - Importance: Assess potential risks like ransomware and data breaches.
   - Phases:
     - Pivoting
     - Evasive Testing
     - Information Gathering
     - Vulnerability Assessment
     - (Privilege) Exploitation
     - Post-Exploitation

2. **Pivoting:**
   - Use exploited host as proxy to scan internal network.
   - Allows access to non-routable networks.
   - Also known as Tunneling.

3. **Evasive Testing:**
   - Conceal actions to avoid detection by blue team.
   - Understand security measures like network segmentation, threat monitoring, IPS/IDS, EDR.
   - Adapt methods to bypass security measures.

4. **Information Gathering:**
   - Obtain overview of reachable systems within the network.
   - Utilize insights from previous stages.
   - Enumerate hosts and servers individually.

5. **Vulnerability Assessment:**
   - Focus on internal network vulnerabilities.
   - Consider group assignments and user rights.
   - Utilize shared information and documents for attack planning.

6. **(Privilege) Exploitation:**
   - Utilize discovered paths to access other systems.
   - Methods include password cracking, pass-the-hash technique, and credential reuse.
   - Aim to move through internal network leveraging existing data and information.

7. **Post-Exploitation:**
   - Repeat post-exploitation steps for each system accessed.
   - Collect system information and business data.
   - Adhere to contract rules regarding sensitive data handling.

8. **Proof-of-Concept:**
   - Demonstrate findings to client for remediation purposes.
   - Help client reproduce results efficiently.

**Note:** Maintain discretion and adhere to contract rules regarding data handling throughout the assessment. Provide clear documentation of findings to assist clients in strengthening their security posture.


## POC
1. **Introduction to PoC:**
   - Used to demonstrate feasibility in project management.
   - Basis for further action in securing corporate networks.
   - Identifies and minimizes risks.

2. **Application in Information Security:**
   - Proves vulnerabilities in operating systems or application software.
   - Validates, reproduces, and assesses impact for developers/administrators.
   - Example: Executing the calculator (calc.exe) to demonstrate software vulnerabilities.

3. **Representation of PoC:**
   - Documentation of vulnerabilities found.
   - Practical version: Script or code for automatic exploitation.
   - Disadvantage: Administrators can adapt systems to counter the script.

4. **Considerations for PoC Usage:**
   - Highlight multiple ways to exploit vulnerabilities, not just the script.
   - Provide clear remediation advice in reports.
   - Emphasize broader issues and attack chain walkthroughs.

5. **Example Scenario:**
   - Weak password policy allows "Password123" as a password.
   - Changing a compromised Domain Admin's password doesn't address underlying policy issue.
   - Emphasize the importance of high-quality standards in systems and applications.


## Post engagement

1. **Cleanup:**
   - Delete tools/scripts from target systems.
   - Revert minor configuration changes made during testing.
   - Document all cleanup activities, even if some artifacts cannot be removed.

2. **Documentation and Reporting:**
   - Gather all necessary documentation for findings.
   - Ensure retrieval of scan and log output.
   - Draft a comprehensive report detailing findings, impact, and remediation recommendations.

3. **Report Review Meeting:**
   - Hold a meeting to discuss assessment results with the client.
   - Walk through findings briefly, addressing questions or concerns.
   - Focus on high-risk findings and recommendations.

4. **Deliverable Acceptance:**
   - Provide a DRAFT report for client review and feedback.
   - Incorporate client feedback into a final report marked as FINAL.
   - Ensure uniform approach to deliverable acceptance across clients.

5. **Post-Remediation Testing:**
   - Review documentation provided by the client on remediation efforts.
   - Reassess target environment to verify remediation effectiveness.
   - Issue a post-remediation report detailing findings status before and after remediation.

6. **Role of the Pentester in Remediation:**
   - Remain impartial and avoid performing remediation actions.
   - Offer general advice and explanations to remediation teams.
   - Maintain assessment integrity and avoid conflicts of interest.

7. **Data Retention:**
   - Retain evidence for a specified period after the assessment.
   - Ensure compliance with local, regional, and company laws.
   - Securely store retained data and wipe from tester systems at the conclusion of assessment.

8. **Close Out:**
   - Ensure proper disposal of systems used during assessment.
   - Securely store artifacts according to firm's policy and contractual obligations.
   - Invoice the client and collect payment for services rendered.
   - Conduct a post-assessment client satisfaction survey for feedback.

9. **Continuous Improvement:**
   - Reflect on assessment interactions and communication.
   - Work on improving soft skills and professional development.
   - Strive for continuous improvement in all aspects of the role as a professional penetration tester.



