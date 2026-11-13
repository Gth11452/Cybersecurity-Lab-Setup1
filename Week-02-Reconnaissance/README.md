# Week 2 — Information Gathering & Reconnaissance

**Ethical Hacking Internship | Networkwalks | Batch B084**

## Project Overview

This project explores passive reconnaissance and basic information gathering using Kali Linux. The objective is to understand publicly accessible domain information, DNS records, web technologies, HTTP headers, and Web Application Firewall detection.

**Target Domain:** `networkwalks.com`

## Tools Used

- Kali Linux
- WHOIS
- WhatWeb
- NSLookup
- cURL
- WAFW00F
- DNSRecon
- Oracle VM VirtualBox

## Practical Tasks

### 1. WHOIS Enumeration

```bash
whois networkwalks.com
```

Collected domain registration information, registrar details, nameservers, and domain status.

![WHOIS](screenshots/01-whois.png)

### 2. Website Technology Fingerprinting

```bash
whatweb networkwalks.com
```

Identified technologies including Apache, WordPress, Bootstrap, and jQuery.

![WhatWeb](screenshots/02-whatweb.png)

### 3. DNS Lookup

```bash
nslookup networkwalks.com
```

Resolved the target domain to an IP address. Some DNS queries timed out, indicating an intermittent DNS resolver issue.

![NSLookup](screenshots/03-nslookup.png)

### 4. HTTP Header Analysis

```bash
curl -I https://networkwalks.com
```

Inspected HTTP response headers, server details, cookies, and relevant security configurations.

![HTTP Headers](screenshots/04-http-headers.png)

### 5. Web Application Firewall Detection

```bash
wafw00f networkwalks.com
```

The tool identified ModSecurity (SpiderLabs) as the website's Web Application Firewall.

![WAFW00F](screenshots/05-wafw00f.png)

### 6. DNS Enumeration

```bash
dnsrecon -d networkwalks.com
```

Collected DNS records including A, NS, MX, TXT, and SRV records.

![DNSRecon](screenshots/06-dnsrecon.png)

## Key Learnings

- Understanding reconnaissance methodologies
- Performing domain and DNS information gathering
- Identifying web technologies
- Analyzing HTTP response headers
- Detecting Web Application Firewalls
- Understanding common DNS resolution errors

## Conclusion

Successfully performed introductory reconnaissance activities using Kali Linux and documented the findings from six practical tools.

**Disclaimer:** This project is intended for educational purposes. All cybersecurity testing should be conducted only with appropriate authorization.

## Acknowledgements

Special thanks to Sir Waqas Karim (CCIE) and the Networkwalks team for their guidance and support.
