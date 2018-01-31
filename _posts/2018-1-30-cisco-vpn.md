--- 

layout: post 

title: Cisco WebVPN Vulnerability with a CVSS score of 10.0

description: Security Flaw 

image: assets/images/pic22.jpg 

--- 

On Jan 29th 2018, Cisco released a new vulnerability regarding their Adaptive Security Appliance(ASA). This vulnerability can be exploited provided the WebVPN feature is enabled on the ASA device. 
In my opinion no security issue, doesn’t matter how big or small, must be ignored but if the flaw has a <b>CVSS score of 10.0</b> then it certainly catches the attention of hackers and administrators all around the globe.
<br  />The vulnerability itself allows an unauthenticated attacker to remotely execute code and reload the affected system. This reload prevents the regular user to access resources hence this acts as a Denial of Service (DOS) attack. [1]
<br  />Let us first look at WebVPN and then see what actually causes this issue.
<br  />So WebVPN, like a normal VPN, allows a user to access resources on another network securely. It does this by using a normal browser instead of using an extra software or hardware client[2]. This is extremely useful as a user can use any computer on the internet, and not be restricted by software or hardware. WebVPN uses SSL and TLS1 for encryption and uses an ASA to recognise connections that need to be proxied and authenticated appropriately by an authentication subsystem.[2]
<br  />In order to exploit the WebVPN issue an attacker will have to send multiple crafted XML packets to a WebVPN configured interface of the ASA. This will basically cause an attempt to double free a region of memory on the ASA device. To make matters worse, since WebVPN does not utilise any software, hardware or certificates, there is no way that the client system can be authenticated. This potentially allows an attacker to conduct the attack from anywhere that has access to the internet. [2]
<br  />If this is successfully attempted then the attacker can have unrestricted access to the protected network where he/she is free to execute any code on the network. This also paves the way to utilise several known attack vectors to conduct attacks. Also, yes there is an also, Cisco has released some software updates that address this, but there are no workarounds for this vulnerability.
<br  />If you utilise the following ASA products then you should apply the appropriate patches as and when CISCO releases them: [1]
- 3000 Series Industrial Security Appliance (ISA)
- ASA 5500 Series Adaptive Security Appliances
- ASA 5500-X Series Next-Generation Firewalls
- ASA Services Module for Cisco Catalyst 6500 Series Switches and Cisco 7600 Series Routers
- ASA 1000V Cloud Firewall
- Adaptive Security Virtual Appliance (ASAv)
- Firepower 2100 Series Security Appliance
- Firepower 4110 Security Appliance
- Firepower 9300 ASA Security Module
- Firepower Threat Defense Software (FTD)
<br  />It should be noted that this issue affects vulnerable releases of Cisco ASA software where WebVPN is enabled. Also an SSL and DTLS listen socket must be present on the TCP port 443(port for HTTPS). If your ASA is running a version prior to 9., 9.3 or 9.5 then Cisco recommends a version update. Full details on how to check if you are affected can be found here by following the link in reference [1].

<br  /><b>References</b>
<br  /><br  />[1] Cisco Security Advisory. “Cisco Adaptive Security Appliance Remote Code Execution and Denial of Service Vulnerability”; retrieved from https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20180129-asa1
<br  />[2] Cisco. "Cisco Security Appliance Command Line Configuration Guide, Version 7.2”; retrieved from https://www.cisco.com/c/en/us/td/docs/security/asa/asa72/configuration/guide/conf_gd/webvpn.html#wp1030670