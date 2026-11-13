# PENETRATION TESTING REPORT
### Footprinting & Network Scanning Phases

**W2-PM-FINAL  |  CYBERSECURITY  |  NETWORKWALKS**

| Field | Detail |
|---|---|
| **Pentester Name (Cybersecurity Professional)** | **Adebayo Ibrahim** |
| **Program/Batch** | B084-Networkwalks |
| **Date** | 13 November 2026 |
| **Modules completed** | W2-PM1 (Multiple Kali Tools)<br>W2-PM2 (GHDB)<br>W2-PM3 (Maltego)<br>W2-PM4 (Harvester)<br>W2-PM5 (Zenmap Scanning) |
| **Client/Target** | 1. Networkwalks (secured written permission already)<br>2. My own local LAN Network |
| **Permission secured from client?** | Yes |
| **Phases covered** | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery<br>**Phase 3-5:** In Progress |

# 1. Liability Disclaimer

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

# 2. Introduction

This report covers footprinting the networkwalks.com domain using multiple Kali Linux tools (W2-PM1), GHDB (W2-PM2), Maltego (W2-PM3), theHarvester (W2-PM4) and scanning my own local network with Zenmap (W2-PM5). One module covers the footprinting phase and the other covers the scanning phase, so together they show how an attacker moves from gathering public information to mapping live hosts on a network. It is the Week 2 part of my ongoing internship program at Networkwalks.

All commands were run in Kali Linux (footprinting) and on a Windows PC with Zenmap installed (scanning). Every step below includes the exact command used, the result I observed, a screenshot as evidence, and a short note on why the finding matters from an attacker's point of view.

# 3. Tools Used

The table below lists each tool used in this report and its purpose.

| Tool | Purpose |
|---|---|
| Kali Linux & Windows | Operating systems used for reconnaissance activities             |
| WHOIS                | Find domain registration details (owner, dates, name servers).   |
| whatweb              | Fingerprint web technologies (server, CMS, plugins, IP).         |
| nslookup             | Resolve the domain name to its IP address using DNS.             |
| curl -I              | Read the HTTP response headers of the website.                   |
| wafw00f              | Detect whether a Web Application Firewall protects the site.     |
| dnsrecon             | Enumerate all DNS records (NS, MX, SPF, TXT, SRV).               |
| GHDB  | Uncover sensitive, hidden, or poorly secured data indexed on the web. |
| Maltego    | Gather, connect, and visualize relationships between disparate data points. |
| theHarvester    | Queries public search engines and database. |
| Windows CMD          | Local IP and MAC address identification                          |
| Zenmap (Nmap GUI)    | Scan the local subnet to find live hosts, IPs and MAC addresses. |

# 4. Activities Performed

## 4.1 Footprinting & Reconnaissance

# PM.1

I performed reconnaissance against the `networkwalks.com` domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon**. Each tool was used to collect a different type of information about the target.

First, I used **WHOIS** to obtain publicly available domain registration information and identify the domain’s name servers. The results provided information about the domain registration and hosting infrastructure.

I then used **WhatWeb** to identify technologies used by the website. The results identified **WordPress 7.0.4** and **WP Download Manager 3.3.58**, along with other information exposed by the website.

Using **Nslookup**, I resolved the domain name to its IP address. The provided result identified **192.232.216.135**.

I used **Curl** with the `-I` option to inspect the HTTP response headers. This provided additional information about the web application and exposed the WordPress REST API endpoint `/wp-json/`.

Next, I used **Wafw00f** to determine whether a Web Application Firewall was protecting the website. The result identified **ModSecurity (SpiderLabs)**.

Finally, I used **DNSRecon** to enumerate DNS records. The results provided information relating to name servers, mail servers, SPF/TXT records, service records and DNS software information.

# PM.2

I performed reconnaissance against poorly secured/exposed web cam and public files using the google hacking database.

# Task 1. 
Find 10x live vulnerable security camera links that are exposed & accessible 
from Internet. List them in below table along with their relevant dork that you have used

# Solution

| No. | Link | Relevant Dork | Username/password(If any) 
|-|---|---|-|
| 1. | http://99.114.240.169:8080/ | intitle:"Webcam" inurl:WebCam.htm | |
| 2. | http://109.233.191.130:8080/ | intitle:"WebcamXP" inurl:8080 | |
| 3. | http://109.206.96.249:8080/ | intitle:"Webcam" inurl:8080 | |
| 4. | http://184.57.102.6:5800/ | intitle:"WebcamXP" | |
| 5. | http://75.149.26.30:1024/ | intitle:"WebcamXP" | |
| 6. ||||
| 7. ||||
| 8. ||||
| 9. ||||
| 10. ||||

# Task 2.
 Find 10x listings which contain downloadable mathematics ebooks in PDF

# Solution 

| No. | Link | Relevant Dork | Username/password(If any) 
|-|---|---|-|
| 1. | http://99.114.240.169:8080/ | intitle:"Webcam" inurl:WebCam.htm | |
| 2. | http://109.233.191.130:8080/ | intitle:"WebcamXP" inurl:8080 | |
| 3. | http://109.206.96.249:8080/ | intitle:"Webcam" inurl:8080 | |
| 4. ||||
| 5. ||||
| 6. ||||
| 7. ||||
| 8. ||||
| 9. ||||
| 10. ||||

# PM.3

I performed reconnnaissance against networkwalks.com doamin using maltego to find all email address associated with the domain.

# Task1.
 Downloaded & installed Maltego on a Windows Computer. 
 ![Maltego](Evidence/Maltego.png)
# Task2.
 Found all email addresses related to the target organization domain networkwalks.com (with due permission).
![Maltego FP](Evidence/maltego_FP.png)

# PM.4 

I performed footprinting against microsoft.com domain uisng theHarvester to query public search angines and database about email IDs and sub-domains related to microsoft.com

# Task 1.
 Found email IDs & sub-domains related to a target organization microsoft.com using the theHarvester tool in Kali Linux with Baidu. Set the limit of number of results to 1000.

``` $ theHarvester -d microsoft.com -l 1000 -b baidu ```

![theharvester FP](Evidence/theHarvester.png)

Task 2. Find email IDs & sub-domains related to a target organization microsoft.com 
using the theHarvester tool in Kali Linux with all sources. Set the limit of number of 
results to 50

``` $ theHarvester -d microsoft.com -l 50 -b all ```

![theharvester FP](Evidence/theHarvester2d.png)
![theharvester FP](Evidence/theHarvester2b.png)

## 4.2 Network Scanning with Zenmap

# PM.5 
For the second phase, I used **Zenmap** to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.

I identified three live hosts(including my pc):

- `192.168.0.1`
- `192.168.0.4`
- `192.168.0.3`

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.

# Task1
 Downloaded & installed Zenmap from official website on my Windows PC

 ![Zenmap](Evidence/Zenmap.png)

# Task2
 Found my IP address & my LAN subnet.
 ![ipconfig](Evidence/ip-config.png)
 ![ipconfig](Evidence/ip-config2.png)
 
# Task3
 Found the list of live hosts/PC’s in my IP subnet by ping scanning my LAN subnet
 ![Live hosts](Evidence/zenmap_ping_scan.png)

# Task4 
 How many hosts are live in your subnet

**ANS: 3** 

# Task5 
 What are the IP addresses of the live hosts?
 - `192.168.0.1`
 - `192.168.0.4`
 - `192.168.0.3`

# Task6
 What are the MAC addresses of the live hosts? 
 - `MAC Address: 5C:7D:AE:14:E9:03 `
 - `MAC Address: 4A:DA:EC:3A:C9:37 `
 - `MAC Address: 4A:DA:EC:3A:C9:37 `

# Task7
 Display & save the output topology in PDF Format on your desktop

**The pdf is here:**
[Topology](Evidence/Topology.pdf)

# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

| **\#** | **Risk / Finding**                           | **Evidence / Observation**                                  | **Potential Impact**                                                                                            | **Risk Level** |
|--------|----------------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|----------------|
| 1      | Web technology information exposed           | WhatWeb identified WordPress and WP Download Manager        | Attackers may use exposed technology/version information to identify software requiring further security review | **● Medium**   |
| 2      | Server IP address identifiable               | Nslookup resolved the domain to `192.232.216.135`           | Provides information about the network location of the web service                                              | **● Low**      |
| 3      | HTTP technical information exposed           | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration                                                    | **● Low**      |
| 4      | WAF technology identifiable                  | Wafw00f identified ModSecurity (SpiderLabs)                 | Reveals information about the web application’s security architecture                                           | **● Low**      |
| 5      | DNS infrastructure information exposed       | DNSRecon identified DNS, mail and service-related records   | DNS information can help build a broader infrastructure profile                                                 | **● Medium**   |
| 6     | Default webcam password and usernames are unchanged      | Multiple webcam are available and accessible on the web | Attackers can keep tab on the target using those webcams       | **● Medium**   |
| 7     | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network    | Unknown or unauthorized devices may potentially be present on a network                                         | **● Medium**   |

**Risk level key:** ● Critical ● Medium ● Low

The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

# 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

1.  **Review publicly exposed technology information**  
    Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.

2.  **Keep software updated**  
    CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.

3.  **Review HTTP headers**  
    HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

4.  **Review DNS records regularly**  
    DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

5.  **Properly configure and monitor the WAF**  
    Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.


6.  **Change Webcam Default Usernames and Passwords**  
    Webcam default usernames and passwords should be change to prevent an attacker from accessing your webcam through the web which may lead to keeping tab on your activities.

7.  **Perform regular internal network discovery**  
    Organizations should periodically scan their own networks to identify active devices.

8.  **Investigate unknown devices**  
    Any unexpected device discovered during network scanning should be investigated and verified.

9.  **Maintain network documentation**  
    Network topology and device information should be documented and updated regularly.

10.  **Perform security testing with authorization**  
    Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

# 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.

In the footprinting activity PM 1, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.

In PM 2, I used GHDB to uncover hidden or sensitive data on the web which helps me to enhance my knowledge of google dorking.

In PM 3, I used maltego to discover the all email addresses associated with the target's domain.

In PM 4, I used theHarvester an OSINT tool to query public search engines for the target's email IDs and sub-domains.

In the network scanning activity PM 5, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

The exercises showed me that information gathering(reconnaissance) is an important part of cybersecurity. And it is divided into two(passive and active recon). Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.

Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

# 8. Evidences Collected

*Screenshots collected as evidence during the activities (stored in the `Evidence/` folder):*

# PM1 Evidences
![whois output](Evidence/whois.png)
![whois output](Evidence/whois2.png)
![whatweb output](Evidence/whatweb.png)
![nslookup output](Evidence/nslookup.png)
![curl output](Evidence/curl.png)
![wafw00f output](Evidence/wafw00f.png)
![dnsrecon output](Evidence/dnsrecon.png)
[FP with multiple kali tools pdf](Evidence/FOOTPRINTING%20WITH%20MUTIPLE%20KALI%20LINUX%20TOOLS.pdf)

# PM2 Evidences

# PM3 Evidences
![maltego](Evidence/Maltego.png)
![maltego_FP](Evidence/maltego_FP.png)

# PM4 Evidences
![theHarvester_FP](Evidence/theHarvester.png)
![theHarvester_FP](Evidence/theHarvester2d.png)
![theHarvester_FP](Evidence/theHarvester2b.png)

# PM5 Evidences
![Zenmap](Evidence/Zenmap.png)
![ip_config](Evidence/ip-config.png)
![ip_config](Evidence/ip-config2.png)
![Zenmap ping scan](Evidence/zenmap_ping_scan.png)
![Zenmap topology](Evidence/zenmap_topology.png)
 [Zenmap topology pdf](Evidence/Topology.pdf)

# 👤 Author

**ADEBAYO IBRAHIM**\
Cybersecurity Professional B084

LinkedIn: [www.linkedin.com/in/ibrahim-adebayo-118613449](www.linkedin.com/in/ibrahim-adebayo-118613449/)

---

## 📌 Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 02 | **Project:**  PENETRATION TESTING (Footprinting & Network Scanning Phases) | **Repository:** GitHub

-End-
