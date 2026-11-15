 <div align="center">

# 🔐 PENETRATION TESTING REPORT

### Footprinting and Network Scanning Phases

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

---

**Week 2 Practical Assessment**

</div>

---
<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/%20Brian%20BSC-C00000?style=flat-square" />
</p>


**NETWORKWALKS | PRACTICAL ACTIVITIES**

---

## ⚠️ Disclaimer

All activities documented in this report were conducted for educational and research purposes under the NetworkWalks Cybersecurity and Ethical Hacking training programme. Testing was limited to systems I own or had authorisation to assess.

Use these tools and techniques responsibly and only with proper authorisation. Unauthorised access is a criminal offence, even where no damage occurs.

The author, instructor and NetworkWalks are not responsible for misuse of this information. All actions remain the sole responsibility of the individual.

---

## 📖 1. Introduction

This report documents practical activities undertaken during Week 2 of the NetworkWalks Cybersecurity and Ethical Hacking training programme.

The exercises covered two main areas:

- **W2-PM1 – Multiple Kali Tools:** Footprinting and reconnaissance of the `networkwalks.com` domain using six Kali Linux tools.
- **W2-PM5 – Zenmap Scanning:** Network discovery and examination of my local network environment.

The exercises demonstrate how publicly available information can be gathered and how active devices can be identified within a local network.

Each activity documents the commands used, observations, findings and supporting screenshots.

---

## 🎯 2. Project Objectives

The main objectives of these practical exercises were to:

- ✅ Perform domain footprinting using multiple Kali Linux tools.
- ✅ Retrieve publicly available domain registration information.
- ✅ Identify website technologies and infrastructure.
- ✅ Perform DNS resolution and enumeration.
- ✅ Inspect HTTP response headers.
- ✅ Identify web application firewall technology.
- ✅ Examine local network configuration.
- ✅ Discover active devices using Nmap and Zenmap.
- ✅ Review network scan results and topology.
- ✅ Document findings and identify potential security risks.

---

## 🛠️ 3. Tools and Technologies Used

| Tool | Purpose |
|---|---|
| 🐉 Kali Linux | Penetration testing environment |
| WHOIS | Domain registration information |
| WhatWeb | Website technology identification |
| Nslookup | DNS resolution |
| Curl | HTTP response header inspection |
| Wafw00f | Web application firewall detection |
| DNSRecon | DNS enumeration |
| Windows `ipconfig` | Local network configuration |
| Nmap | Network host discovery |
| Zenmap | Graphical network scanning and visualisation |

---

# 🔎 4. Activities Performed

## 🌍 4.1 Footprinting and Reconnaissance – W2-PM1

I performed reconnaissance on the `networkwalks.com` domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon**.

Each tool was used to collect a different category of information about the domain, website technologies, DNS configuration and web security infrastructure.

### ⚙️ Task 1: WHOIS – Domain Registration Information

**🎯 Objective:** Retrieve publicly available domain registration information, including the registrar, registration dates, name servers and domain status.

**🔍 Analysis:**

The WHOIS lookup returned information about the domain's registration and name servers. The registrant's identity was protected through a domain privacy service.

The listed domain status restrictions provide certain protections against unauthorised domain changes. The DNSSEC result indicated that the domain was reported as unsigned. This is a configuration observation rather than confirmation of a vulnerability.

### ⚙️ Task 2: WhatWeb – Website Technology Identification

**🎯 Objective:** Identify technologies, software components and services used by the target website.

**🔍 Analysis:**

WhatWeb identified WordPress and other technologies used by the website. These findings provided an overview of the website's technology stack and highlighted components that could require further security review.

The initial HTTP request redirected to HTTPS, where the website returned a successful response.

However, identifying a particular technology or software component does not establish that it is vulnerable.

### ⚙️ Task 3: Nslookup – DNS Resolution

**🎯 Objective:** Resolve the domain name to its corresponding IP address and identify the DNS resolver used.

**🔍 Analysis:**

Nslookup successfully resolved the domain name to an IPv4 address.

The non-authoritative response indicates that the answer was supplied by a recursive DNS resolver rather than directly by an authoritative name server.

The resolved IP address was consistent with the address identified during the WhatWeb exercise.

### ⚙️ Task 4: Curl – HTTP Response Header Inspection

**🎯 Objective:** Inspect the HTTP response headers returned by the website over HTTPS.

**🔍 Analysis:**

The website returned a successful HTTPS response. The cookie attributes observed provide protections against certain types of cookie exposure and client-side access.

The response also exposed references to WordPress REST API endpoints. Their presence alone does not establish a security weakness. The permissions and information available through those endpoints would require separate assessment.

### ⚙️ Task 5: Wafw00f – Web Application Firewall Detection

**🎯 Objective:** Determine whether a web application firewall could be detected on the target website.

**🔍 Analysis:**

Wafw00f identified **ModSecurity (SpiderLabs)** as the web application firewall associated with the target.

A web application firewall can help monitor and filter potentially malicious web traffic. However, detecting a WAF does not establish that its rules are correctly configured or that it can prevent all forms of attack.

No WAF bypass attempt was conducted during this exercise.

### ⚙️ Task 6: DNSRecon – DNS Enumeration

**🎯 Objective:** Enumerate publicly available DNS records associated with the target domain.

**🔍 Analysis:**

DNSRecon identified mail-related service records and SPF information.

The results provided further information about the domain's name servers, mail configuration and service discovery records.

The SPF record provides information about sources authorised to send email on behalf of the domain.

---

## 🌐 4.2 Network Scanning and Network Discovery – W2-PM5

The second activity involved examining my local network configuration and identifying active devices within the network.

The practical covered local IP address identification, subnet identification, host discovery and graphical review of scan results using Zenmap.

### ⚙️ Step 1: Identifying the Local Network Configuration

**🎯 Objective:** Identify the local computer's IP address, subnet mask and default gateway before performing network discovery.

**🔍 Analysis:**

The Windows network configuration provided the information needed to identify the local network range before conducting the Nmap host discovery scan.

The `/24` subnet contains 256 IPv4 addresses, including the network and broadcast addresses.

### ⚙️ Step 2: Nmap – Local Network Host Discovery

**🎯 Objective:** Identify active devices within the local network without performing a port scan.

**🔍 Analysis:**

The Nmap scan demonstrated how host discovery can be used to identify active devices within a specified network range.

The `-sn` option performs host discovery without conducting a port scan.

The scan identified three active hosts within the examined network range. These devices responded to the discovery probes used during the exercise.

The scan did not establish the operating systems, open ports or vulnerabilities of the discovered devices. Those would require separate authorised assessment activities.

### ⚙️ Step 3: Zenmap – Network Scan Visualisation

**🎯 Objective:** Review network scan results using Zenmap, the graphical interface for Nmap, and generate a network topology as required by the practical.

**🔍 Analysis:**

Zenmap provides a graphical interface for reviewing Nmap scan results, making it easier to examine discovered hosts and their relationships within the scanned network.

The Topology section provides a visual representation of the network discovery results, helping to present the findings in a clear and organised format.

---

# ⚠️ 5. Risk Analysis and Impact

Based on the observations collected during footprinting and network discovery, the following potential security considerations were identified.

| No. | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Website technology information exposed | WhatWeb identified WordPress and a plugin | May assist further technology fingerprinting and software research | 🟠 Medium |
| 2 | Domain IP address identifiable | Nslookup resolved the domain to an IPv4 address | Provides information about the hosting infrastructure | 🟢 Low |
| 3 | HTTP technical information exposed | Curl returned response headers and REST API references | May assist further enumeration | 🟢 Low |
| 4 | WAF technology identifiable | Wafw00f detected ModSecurity | Reveals information about the web security architecture | 🟢 Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail and service records | May help build a broader infrastructure profile | 🟠 Medium |
| 6 | Multiple active local hosts identified | Nmap discovered three active hosts | Unrecognised devices may require investigation | 🟠 Medium |

**Risk level key:**

- 🟢 **Low:** Limited observed exposure.
- 🟠 **Medium:** Warrants further review.
- 🔴 **High/Critical:** Requires urgent assessment where confirmed.

### 📌 Risk Assessment Notes

The risk levels above are indicative assessments of potential exposure, not confirmed vulnerability ratings.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these activities.

The presence of information such as a software version, IP address, DNS record or WAF technology does not by itself mean that a system is vulnerable. Further authorised security testing would be required to establish whether an actual vulnerability exists.

---

# 🛡️ 6. Recommendations

Based on the observations from the practical exercises, the following security improvements are recommended.

**1. 🔍 Review publicly exposed technology information**

Organisations should regularly review the information publicly visible about their web technologies, content management systems and plugins.

**2. 🔄 Keep software updated**

Content management systems, plugins and other web technologies should be updated regularly and checked against relevant security advisories.

**3. 🔐 Review HTTP response headers**

HTTP response headers should be assessed to determine whether unnecessary technical information is exposed and whether appropriate security policies are configured.

**4. 🌐 Review DNS records regularly**

DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

**5. 🛡️ Review DNSSEC configuration**

Where appropriate, organisations should assess the implementation of DNSSEC to support DNS response authenticity.

**6. 🔥 Properly configure and monitor the WAF**

ModSecurity rules should be reviewed, maintained and monitored to ensure that the web application firewall is appropriately configured.

**7. 📡 Perform regular internal network discovery**

Organisations should periodically scan their own networks to identify active devices and maintain an accurate network inventory.

**8. 💻 Investigate unknown devices**

Unexpected devices discovered during network scanning should be investigated and verified.

**9. 🗺️ Maintain network documentation**

Network topology and device information should be documented and updated regularly.

**10. ⚖️ Conduct security testing with authorisation**

Reconnaissance and scanning should only be performed against systems and networks where appropriate authorisation has been obtained.

---

# 🎯 7. Conclusion

During Week 2 of the NetworkWalks Cybersecurity and Ethical Hacking training programme, I completed practical activities covering footprinting, reconnaissance and network discovery.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. WHOIS provided domain registration information, WhatWeb identified website technologies, Nslookup resolved the domain name, Curl inspected HTTP response headers, Wafw00f detected a web application firewall, and DNSRecon provided additional DNS information.

In the network discovery activity, I used Windows `ipconfig` to examine the local network configuration and Nmap to identify active hosts. The scan examined 256 IP addresses and identified three active hosts.

The exercises demonstrated that information gathering is an important part of cybersecurity assessment. Before conducting deeper security testing, a practitioner can learn a considerable amount about a target environment by analysing publicly available information and network responses.

I also learned the importance of documenting technical findings accurately, interpreting observations carefully and distinguishing potential risks from confirmed vulnerabilities.

Finally, the exercises reinforced the importance of conducting reconnaissance and network scanning within an authorised scope.

---

## 📸 8. EVIDENCE COLLECTED

📂 **Evidence directory:** `screenshots/`

Screenshots and supporting evidence collected during the practical assessment are organised in the repository's `screenshots/` directory.

| **No.** | **Evidence** | **Filename** |
|:---:|---|---|
| **1** | 🔎 WHOIS lookup | `1_whois.png` |
| **2** | 🛠️ WhatWeb results | `2_whatweb.png` |
| **3** | 🌐 Nslookup results | `3_nslookup.png` |
| **4** | 📡 cURL response headers | `4_curl.png` |
| **5** | 🛡️ Wafw00f results | `5_wafw00f.png` |
| **6** | 🗂️ DNSRecon results | `6_dnsrecon.png` |
| **7** | 💻 Windows network configuration | `7_ipconfig.png` |
| **8** | 🔍 Nmap host discovery | `8_nmap.png` |
| **9** | 🖥️ Zenmap topology | `9_zenmap_topology.png` |
| **10** | 📄 Exported network topology | `10_network_topology.pdf` |
</div>

<div align="center">

### 👨‍💻 Author: Brian Simpande

**NETWORKWALKS | PRACTICAL ACTIVITIES**

</div>

*B084 | Cybersecurity and Ethical Hacking | NetworkWalks*

</div>
