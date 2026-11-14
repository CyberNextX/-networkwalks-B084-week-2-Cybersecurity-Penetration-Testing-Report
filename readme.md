 <div align="center">

# 🔐 PENETRATION TESTING REPORT

### Footprinting and Network Scanning Phases

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

ield	Detail
Pentester Name (Cybersecurity Professional)	Brian Simpande
Programme/Batch	B084 – NetworkWalks
Date	15 November 2026 (or the actual submission date)
Modules completed	W2-PM1 (Multiple Kali Tools)  

 W2-PM5 (Zenmap Scanning)
Client/Target	1. NetworkWalks  

 2. Own local LAN network
Permission secured from client?	Confirm and state the accurate permission status. Do not claim written permission unless you have it.
Phases covered	Phase 1: Reconnaissance and Footprinting  

 Phase 2: Scanning and Network Discovery  

 Phases 3–5: In Progress

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

## ⚖️ 1. Liability Disclaimer

The activities documented in this report were conducted for educational and research purposes as part of the NetworkWalks Cybersecurity and Ethical Hacking training programme.

Testing was limited to systems within the authorised training scope and the participant's own local network. The techniques and tools demonstrated in this report must only be used on systems and devices for which appropriate authorisation has been obtained.

Unauthorised access to computer systems and networks may constitute a criminal offence, even where no damage is caused. The author, instructor and training institution are not responsible for the misuse of information contained in this report. The individual conducting any security assessment remains responsible for ensuring that all activities comply with applicable laws and authorisation requirements.

## 📖 2. Introduction

This report documents practical activities undertaken during Week 2 of the Cybersecurity and Ethical Hacking training programme at NetworkWalks.

The exercises covered two main areas:

- **W2-PM1 – Multiple Kali Tools:** Footprinting and reconnaissance of the `networkwalks.com` domain using six Kali Linux tools.
- **W2-PM5 – Zenmap Scanning:** Network discovery and examination of the participant's local network environment.

The exercises demonstrate how information can be gathered from publicly accessible internet services and how active devices can be identified within a local network.

The footprinting activities were conducted using Kali Linux, while Windows network configuration information was examined using the `ipconfig` command. Nmap was used for local network host discovery.

Each activity documents the command used, the observations obtained, the significance of the findings and the supporting evidence where available.

## 🛠️ 3. Tools Used

The following tools and technologies were used during the practical exercises.

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system used for footprinting and reconnaissance |
| WHOIS | Retrieves domain registration and registrar information |
| WhatWeb | Identifies website technologies and components |
| Nslookup | Resolves domain names through DNS |
| cURL | Inspects HTTP response headers |
| Wafw00f | Detects web application firewall technologies |
| DNSRecon | Enumerates DNS records and service information |
| Windows CMD | Displays local network configuration |
| Nmap | Discovers active hosts on a network |
| Zenmap | Graphical interface for reviewing Nmap scans and network topology |

## 🔎 4. Activities Performed

### 🌍 4.1 Footprinting and Reconnaissance – W2-PM1

The first phase involved conducting reconnaissance against the `networkwalks.com` domain using six Kali Linux tools: WHOIS, WhatWeb, Nslookup, cURL, Wafw00f and DNSRecon.

Each tool was used to collect a different category of information about the domain, website technologies, DNS configuration and web security infrastructure.

#### ⚙️ Task 1: WHOIS – Domain Registration Information

**Objective:** Retrieve publicly available domain registration information, including the registrar, registration dates, name servers and domain status.

**Command executed:**

```bash
whois networkwalks.com
```

**Observations and findings:**

| Field | Observation |
|---|---|
| Domain name | `networkwalks.com` |
| Registrar | GoDaddy.com, LLC |
| Creation date | 6 November 2019 |
| Updated date | 12 November 2025 |
| Expiry date | 6 November 2027 |
| Registrant privacy | Domains By Proxy, LLC |
| DNSSEC | Reported as unsigned |
| Domain status | Client-side deletion, renewal, transfer and update restrictions listed |

The WHOIS lookup also returned information about the domain's name servers and registrar.

**Analysis:**

The results provided information about the domain's registration history and administrative arrangements. The registrant's identity was protected through a domain privacy service.

The listed domain status restrictions provide certain protections against unauthorised domain changes. The DNSSEC result indicates that the domain was reported as unsigned; this is a configuration observation rather than confirmation of a vulnerability.

**📸 Evidence – WHOIS results**

![WHOIS command output](screenshots/1_whois.png)

#### ⚙️ Task 2: WhatWeb – Website Technology Identification

**Objective:** Identify technologies, software components and services used by the target website.

**Command executed:**

```bash
whatweb networkwalks.com
```

**Observations and findings:**

| Component | Result |
|---|---|
| Website title | Networkwalks Academy |
| Web server | Apache |
| Content management system | WordPress |
| WordPress version reported | 7.1.4 |
| Plugin detected | WordPress Download Manager 3.3.76 |
| JavaScript library | jQuery 3.7.1 |
| Front-end technology | Bootstrap reported |
| Google Tag Manager | Detected |
| HTTP response | `301 Moved Permanently` |
| HTTPS response | `200 OK` |

**Analysis:**

WhatWeb identified WordPress and other technologies used by the website. This information provides an overview of the website's technology stack and can help a security assessor identify components that may require further review.

The initial HTTP request redirected to HTTPS, where the website returned a successful response.

Technology detection does not establish that an identified component is vulnerable. Software versions and component details should be independently verified before drawing security conclusions.

**📸 Evidence – WhatWeb results**

![WhatWeb command output](screenshots/2_whatweb.png)

#### ⚙️ Task 3: Nslookup – DNS Resolution

**Objective:** Resolve the domain name to its corresponding IP address and identify the DNS resolver used.

**Command executed:**

```bash
nslookup networkwalks.com
```

**Observations and findings:**

| Field | Result |
|---|---|
| DNS resolver | Google Public DNS (`8.8.8.8`) |
| Response type | Non-authoritative answer |
| Resolved IPv4 address | `[REDACTED]` |

The resolved IP address matched the address identified during the WhatWeb exercise.

**Analysis:**

Nslookup successfully resolved the domain name to an IPv4 address.

The non-authoritative response indicates that the answer was supplied by a recursive DNS resolver rather than directly by an authoritative name server.

The matching IP address from the two exercises provided consistency between the observations.

**📸 Evidence – Nslookup results**

![Nslookup command output](screenshots/3_nslookup.png)

#### ⚙️ Task 4: cURL – HTTP Response Header Inspection

**Objective:** Inspect the HTTP response headers returned by the website over HTTPS.

**Command executed:**

```bash
curl -I https://networkwalks.com
```

**Observations and findings:**

| Header or response | Observation |
|---|---|
| HTTP status | `200 OK` |
| Web server | Apache |
| Content type | `text/html; charset=UTF-8` |
| Referrer policy | `no-referrer-when-downgrade` |
| Permissions policy | Present |
| WordPress REST API | References to `/wp-json/` and a pages endpoint |
| Cookie security | The observed `__wpdm_client` cookie included `Secure` and `HttpOnly` attributes |
| Cache information | Cache-related headers returned |

**Analysis:**

The website returned a successful HTTPS response. The cookie attributes observed provide protections against certain types of cookie exposure and client-side access.

The response also exposed references to WordPress REST API endpoints. Their presence alone does not establish a security weakness. The permissions and information available through those endpoints would require separate assessment.

The presence of security-related headers is useful, but does not by itself confirm that the website's security configuration is optimal.

**📸 Evidence – cURL response headers**

![cURL command output](screenshots/4_curl.png)

#### ⚙️ Task 5: Wafw00f – Web Application Firewall Detection

**Objective:** Determine whether a web application firewall could be detected on the target website.

**Command executed:**

```bash
wafw00f networkwalks.com
```

**Observations and findings:**

| Field | Result |
|---|---|
| Tool | Wafw00f |
| Version | 2.4.2 |
| Target | `https://networkwalks.com` |
| Detection result | ModSecurity (SpiderLabs) |
| Requests made | 2 |

**Analysis:**

Wafw00f identified ModSecurity (SpiderLabs) as the web application firewall associated with the target.

A web application firewall can help monitor and filter potentially malicious web traffic. However, detecting a WAF does not establish that its rules are correctly configured or that it can prevent all forms of attack.

No WAF bypass attempt was conducted during this exercise.

**📸 Evidence – Wafw00f results**

![Wafw00f command output](screenshots/5_wafw00f.png)

#### ⚙️ Task 6: DNSRecon – DNS Enumeration

**Objective:** Enumerate publicly available DNS records associated with the target domain.

**Command executed:**

```bash
dnsrecon -d networkwalks.com
```

**Observations and findings:**

| DNS information | Observation |
|---|---|
| SOA | Start of Authority record identified |
| NS | Name server records identified |
| A | IPv4 address record identified |
| MX | Mail server record identified |
| TXT | SPF and Google site-verification records found |
| SRV | Eight autodiscovery service records identified |
| DNSSEC | Query returned no answer |
| DNS software | BIND version information reported |

DNSRecon also identified mail-related service records and SPF information.

**Analysis:**

The DNS enumeration provided further information about the domain's name servers, mail configuration and service discovery records.

The SPF record provides information about sources authorised to send email on behalf of the domain. The reported BIND version information may be useful for further assessment, but a version string alone does not confirm that the DNS server is vulnerable.

The DNSSEC query returned no answer. This should be treated as an observation requiring further verification.

**📸 Evidence – DNSRecon results**

![DNSRecon command output](screenshots/6_dnsrecon.png)

### 🌐 4.2 Network Scanning and Network Discovery – W2-PM5

The second phase involved examining the participant's local network configuration and identifying active devices within the local network.

The practical covered local IP address identification, subnet identification, host discovery and the graphical review of scan results using Zenmap.

#### ⚙️ Step 1: Identifying the Local Network Configuration

**Objective:** Identify the local computer's IP address, subnet mask and default gateway before performing network discovery.

**Command executed on Windows:**

```cmd
ipconfig
```

**Observations and findings:**

| Field | Observation |
|---|---|
| Network type | Private IPv4 network |
| Local subnet | `[REDACTED]/24` |
| Subnet mask | `255.255.255.0` |
| Local computer IP address | `[REDACTED]` |

**Analysis:**

The Windows network configuration provided the information required to identify the local network range before conducting the Nmap host discovery scan.

The `/24` subnet contains 256 IPv4 addresses, including the network and broadcast addresses.

**📸 Evidence – Windows network configuration**

![Windows ipconfig output](screenshots/7_ipconfig.png)

#### ⚙️ Step 2: Nmap – Local Network Host Discovery

**Objective:** Identify active devices within the local network without performing a port scan.

**Command executed:**

```bash
nmap -sn [REDACTED]/24
```

**Observations and findings:**

| Field | Result |
|---|---|
| Scan type | Host discovery (`-sn`) |
| IP addresses examined | 256 |
| Active hosts identified | 3 |
| Scan duration | Approximately 2.93 seconds |

The scan identified three active hosts, including the local gateway, another network device and the scanning computer.

Individual IP addresses, MAC addresses and hostnames have been redacted in this public report.

**Analysis:**

The Nmap scan demonstrated how host discovery can be used to identify active devices within a specified network range.

The `-sn` option performs host discovery without conducting a port scan. The three detected hosts indicate that three devices responded to the discovery probes used during the exercise.

The scan did not establish the operating systems, open ports or vulnerabilities of the discovered devices. Those would require separate authorised assessment activities.

**📸 Evidence – Nmap host discovery**

![Nmap command output](screenshots/8_nmap.png)

#### ⚙️ Step 3: Zenmap – Network Scan Visualisation

**Objective:** Review network scan results using Zenmap, the graphical interface for Nmap, and generate a network topology where required by the practical.

The Zenmap stage is intended to provide a graphical representation of discovered hosts and their relationship within the scanned network.

**Evidence status:** Add the Zenmap scan screenshot and exported topology after completing and verifying this stage.

**📸 Evidence – Zenmap topology**

![Zenmap topology screenshot](screenshots/9_zenmap_topology.png)

**Optional exported topology file:**

`screenshots/10_network_topology.pdf`

## ⚠️ 5. Risk Analysis and Impact

Based on the observations collected during footprinting and network discovery, the following potential security considerations were identified.

| No. | Risk / Finding | Evidence / Observation | Potential Impact | Indicative Risk |
|---:|---|---|---|---|
| 1 | Website technology information exposed | WhatWeb identified WordPress and a plugin | May assist further technology fingerprinting and software research | Medium |
| 2 | Domain IP address identifiable | Nslookup resolved the domain to an IPv4 address | Provides information about the hosting infrastructure | Low |
| 3 | HTTP technical information exposed | cURL returned response headers and REST API references | May assist further enumeration | Low |
| 4 | WAF technology identifiable | Wafw00f detected ModSecurity | Reveals information about the web security architecture | Low |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail and service records | May help build a broader infrastructure profile | Medium |
| 6 | Multiple active local hosts identified | Nmap discovered three active hosts | Unrecognised devices may require investigation | Medium |

**Risk level key:** Low – limited observed exposure; Medium – warrants further review.

The risk levels above are indicative assessments of potential exposure, not confirmed vulnerability ratings.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these activities.

The presence of information such as a software version, IP address, DNS record or WAF technology does not by itself mean that a system is vulnerable. Further authorised security testing would be required to establish whether an actual vulnerability exists.

## 🛡️ 6. Recommendations

Based on the observations from the practical exercises, the following security improvements are recommended.

1. **Review publicly exposed technology information**

   Organisations should regularly review the information publicly visible about their web technologies, content management systems and plugins.

2. **Keep software updated**

   Content management systems, plugins and other web technologies should be updated regularly and checked against relevant security advisories.

3. **Review HTTP response headers**

   HTTP response headers should be assessed to determine whether unnecessary technical information is exposed and whether appropriate security policies are configured.

4. **Review DNS records regularly**

   DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

5. **Review DNSSEC configuration**

   Where appropriate, organisations should assess the implementation of DNSSEC to support DNS response authenticity.

6. **Properly configure and monitor the WAF**

   ModSecurity rules should be reviewed, maintained and monitored to ensure that the web application firewall is appropriately configured.

7. **Perform regular internal network discovery**

   Organisations should periodically scan their own networks to identify active devices and maintain an accurate network inventory.

8. **Investigate unknown devices**

   Unexpected devices discovered during network scanning should be investigated and verified.

9. **Maintain network documentation**

   Network topology and device information should be documented and updated regularly.

10. **Conduct security testing with authorisation**

    Reconnaissance and scanning should only be performed against systems and networks where appropriate authorisation has been obtained.

## 🎯 7. Conclusion

During Week 2 of the Cybersecurity and Ethical Hacking training programme, I undertook practical activities covering footprinting, reconnaissance and network discovery.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. WHOIS provided domain registration information, WhatWeb identified website technologies, Nslookup resolved the domain name, cURL inspected HTTP response headers, Wafw00f detected a web application firewall, and DNSRecon provided additional DNS information.

In the network discovery activity, I used Windows `ipconfig` to examine the local network configuration and Nmap to identify active hosts. The scan examined 256 IP addresses and identified three active hosts.

The exercises demonstrated that information gathering is an important part of cybersecurity assessment. Before conducting deeper security testing, a practitioner can learn a considerable amount about a target environment by analysing publicly available information and network responses.

I also learned the importance of documenting technical findings accurately, interpreting observations carefully and distinguishing potential risks from confirmed vulnerabilities.

Finally, the exercises reinforced the importance of conducting reconnaissance and network scanning within an authorised scope.

## 📸 8. Evidence Collected

Screenshots and supporting evidence should be stored in the `screenshots/` directory of this repository.

| No. | Evidence | Filename |
|---:|---|---|
| 1 | WHOIS lookup | `1_whois.png` |
| 2 | WhatWeb results | `2_whatweb.png` |
| 3 | Nslookup results | `3_nslookup.png` |
| 4 | cURL response headers | `4_curl.png` |
| 5 | Wafw00f results | `5_wafw00f.png` |
| 6 | DNSRecon results | `6_dnsrecon.png` |
| 7 | Windows network configuration | `7_ipconfig.png` |
| 8 | Nmap host discovery | `8_nmap.png` |
| 9 | Zenmap topology | `9_zenmap_topology.png` |
| 10 | Exported network topology | `10_network_topology.pdf` |

---

<div align="center">

**— END OF REPORT —**

**BRIAN SIMPANDE**

*B084 | Cybersecurity and Ethical Hacking | NetworkWalks*

</div>
