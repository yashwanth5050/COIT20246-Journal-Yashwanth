# Week 9 Journal – Attacks and Vulnerabilities

**Student Name:** Yashwanth. **GitHub:** https://github.com/yashwanth5050. **Unit:** COIT20246 Networking and Cyber Security. **Week:** 9. **Topic:** Attacks and Vulnerabilities.

## Activity 1 – Applying the CIA Triad to Project Assets

### Objective

The purpose of this activity was to identify important project assets and decide which parts of confidentiality, integrity and availability are most important for each asset.

### Asset Analysis

So user information (credentials) should be kept confidential and integrity, passwords, and authentication information should not be compromised or altered by other invasive users. If credentials were revealed, it might allow an attack similar to the one where the attacker becomes the authorised user, and if they were modified, it may have prevented the correct user from accessing, or opened up access to others.

Data for projects and tests must be confidential and intact so information can be made open only to those authorized to access it, and the integrity of the information is critical in the event results are tested. Integrity and availability of the configuration of routers and switches are essential to ensure that unlicensed changes don't somehow cause traffic to be rerouted, connectivity to fail, or security controls to be weakened.

The Web or application server must be accessible for authorised users to access the service and have integrity in that its files or configuration are not altered by an attacker. The source code and documentation of the GitHub project must be integral and accessible as the team must rely on the history of changes and access to up-to-date project files.

Availability of network links and Internet connectivity is required since users depend on the network to make use of the service or for performing remote testing without connectivity. Confidentiality, Integrity and Availability are also important when it comes to backup copies as it is important for them to be kept private, unalterable and useful – should recovery become necessary.

### Interpretation

Activity demonstrated that multiple CIAs may be required for the protection of a single asset. A good example is credentials as confidentiality ensures that they can't be divulged and integrity ensures they can only be changed with authorisation. So the CIA triad can now be used as a systematic approach to determining what bad that should stop happening to a project asset.

## Activity 2 – Threat Sources and Motivation

### Objective

This activity was done to assess the realistic threat potential of adversarial activity in the project network and to hypothesize about the reasons for such adversarial activity.

### Threat Sources

In this case, an external attacker on the Internet could try to crack into the system or exploit a weakness in one of the services offered through the system to gain access and steal information or create a foothold to conduct more attacks. An insider can misuse it and tamper with data, destroy the project or allow access to data that they should not have.

An unauthorized local wireless user may try to obtain free Internet access or may try to access poorly protected traffic or to gain access to devices on the local area network. The malware or botnet owner might use a yet infected host for spam trafficking, stealing credentials, cryptomining or ransomware or distributed attacks. The reason for the attack may be to get to information about a project or it may be to find vulnerabilities or to disrupt the service by a competitor or curious attacker. An opportunistic automated scanner could just scan the Internet for exposed ports, default credentials or known vulnerabilities and not specifically target the organisation.

### Interpretation

A likelier type of attack depends on the motivation of a threat source. A scanner could find any simple vulnerability, and an insider already has some sort of way to access the system and could identify certain aspects of the system and their content.

To understand some recent NIST NVD vulnerabilities.To learn about recent vulnerabilities in NIST NVD.

### Objective

The goal with this activity was to try to compare three CVEs from the last year, and look through one Critical, one High and one Medium vulnerability.

### Critical – CVE-2026-2774

Using Mozilla Firefox and Thunderbird, CVE-2026-2774 was published on 24 February 2026. CVSS v3.1 is rated as Critical with a score of 9.8 and the CVSS vector is CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H. The impact is rated High and Weakness is rated as CWE-190 Integer Overflow or Wraparound.

The vulnerability is an integer overflow issue of the Audio/Video component. Put differently, a number used in the media processing could be out-of-range, causing erratic subsequent operations and/or memory accesses. As a practical mitigation, it is to identify Firefox (or Thunderbird) versions affected and refresh them to the releases that Mozilla has identified as patched. The NVD entry can be found here: https://nvd.nist.gov/vuln/detail/CVE-2026-2774.

### High – CVE-2026-26283

Published on 23 February 2026, CVE-2026-26283 is a vulnerability in the open-source package ImageMagick, which was used to convert and manipulate digital images. The CVSS v3.1 Base Score is 7.5 High with vector CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:H, Confidentiality and Integrity impact is None, while the availability impact is High. CWE-835 Loop with Unreachable Exit Condition is the weakness identified.

This problem can make a JPEG encoding loop to run indefinitely if the writing repeatedly fails. A clever input can thus make the process use CPU but never make any further progress, leading to a Denial of Service (DoS) issue. Mitigation: Upgrade any affected versions of ImageMagick to a corrected release, apply resource limits or monitor services that service images from untrusted sources. The NVD entry for this vulnerability can be found at https://nvd.nist.gov/vuln/detail/CVE-2026-26283.

### Medium – CVE-2026-40312

CVE-2026-40312 was released on 13 April 2026, and is also applicable to ImageMagick. According to the NVD entry, the CVSS rating of 5.5 (Medium) has these components:AV:L/AC:L/PR:N/UI:R/S:U/C:N/I:N/A:H. The Confidentiality, Integrity, and Availability impact scores are rated as None. Off-by-one Error" is the name of the weakness CWE-193.

The vulnerability applies to the MSL decoder and can lead to crash during the process of a malicious MSL file. In other words, the decoder can grab not only one position outside the desired boundary, but also one. The documented situation results in the primary impact on security being on availability as the process can end. Mitigation consists of upgrading to ImageMagick with the fixed release, not trusting any questionable MSL files on vulnerable systems and watching out for service crashes in an image-processing service. The NVD entry for this vulnerability can be found at https://nvd.nist.gov/vuln/detail/CVE-2026-40312.

### Comparison

The three vulnerabilities demonstrate that there are degrees of severity considering attack conditions and expected impact. CVSS score is rated as Critical because the attacker can exploit CVE-2026-2774 in low complexity, doesn't need any privileges and will get a high score for confidentiality and integrity and availability. The two ImageMagick examples mostly impact availability and therefore the detected severity is lower.

## Activity 4 – Vulnerability Disclosure

### Objective

This activity was to let people think about why vulnerabilities are often published in a "coordinated manner" and not right after discovery.

### Viewpoint

The vendor may require time in order to be able to duplicate the problem, identify the versions impacted, develop a correction, perform testing, and bring about guidance for the customer community. Full technical descriptions might allow attackers time to use before a fix is made available, and organisations cannot do anything in the real world to protect themselves.

The disclosure period should be long enough for a responsive vendor to investigate and issue a correction, but should not give an opportunity for a serious vulnerability to remain in the closet forever. The right time should be when the situation is severe, but also when there is a potential for exploitation, and complexity. If there is exploitation currently occurring it is perhaps important to avoid wasting time in coordination and that disclosure is made quickly.

Once a vendor is non-receptive or always new reasons for delay, a researcher may turn towards public disclosure. Where possible, this should also be take a coordinated approach, with an alert sent to the vendor and sufficient detail to help users minimise risk. The intent of disclosure should be to make it more secure, not embarrassment the vendor.

Coordinated vulnerability disclosure and bug bounty programs make a difference in the process because they have channels for getting it done, guidelines and expectations, and the necessary motivation for researchers to disclose security issues responsibly.

## Problems and Troubleshooting

The primary difficulty was the decent degree of interpretation required on CVSS without focusing solely on the CVSS score. As part of my analysis I used the attack vector and the confidentiality, integrity and availability impacts to understand why the three vulnerability got different level of severity and did a cross-section with the vulnerability description and the associated CWE.

## Weekly Reflection

Week 9 related general security ideas to real vulnerability info. The CIA activity assisted me in thinking about what needs to be protected before selecting controls and the threat-source activity demonstrated that an attacker's motivation and level of access can be very different.

As CVSS was less of an abstraction with the NVD activity, I was able to understand the input for the attack conditions/impact and how these elements add up to a severity rating. One thing more I learned was that, after we have a CVE identified, it is not the end of the vulnerability management process. Organisations will still have to determine which software is impacted, install patches and get a sense of security information to share and its exploitation.