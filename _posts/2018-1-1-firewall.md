---
layout: post
title: Architectures for deploying a firewall in a company
description: General security
image: assets/images/pic19.jpg
---

Let us first define Firewalls before we discuss an architecture for deploying a firewall in a company. A firewall [1] is a hardware or software system that prevents unauthorised access to or from a network. Firewalls are an important part of businesses in today’s day and age, where corporate espionage and cyber attacks are as common as air.

<br  />There is no universal architecture a company can use. While selecting a firewall the company has to keep the following factors in mind: [2]

- Is the firewall giving the desired security level
- Is the firewall scalable depending on the company’s needs
- Is the firewall cost effective
- Does the firewall provide support for the size of the organisation

There are several different types of architectures that a company can choose from but the three main architectures that are used commercially are: [3]

- Bastion host
- Screened subnet
- Dual firewall with DMZ
In a bastion host [3] the firewall is placed between the internet and the protected network. The bastion is the cheapest amongst the mentioned topology and is perfect for relatively simple networks, although once the firewall is bypassed the user will have unrestricted access to the protected network. This topology is suited for small growing business but would not be a good option for a big company.

The screened subnet topology [3] offers additional advantages over the bastion host approach as it uses a single firewall with three networks connected to it (the internet, intranet and a DMZ). The host public services are placed in the Demilitarised Zone (DMZ), which is separated from both the internet and the trusted network by the firewall, therefore if a malicious user does manage to bypass the firewall, they will not have access to the intranet. This architecture allows a company to offer services to the internet users while still maintaining security, it is a good architecture for an e-commerce company as it allows them to securely yet efficiently divide their networks.

The most secure and the most expensive option is to implement a screened subnet [3] using 2 firewalls. In this case the DMZ is placed between 2 firewalls which provides an added layer of security. This still allows the company to offer services to the internet users and at the same time protects the company if a malicious user discovers a software-specific exploitable vulnerability. Just incase the malicious user gets past the first firewall due to an exploit the inspection at the second firewall will block the user from entering the secured network.

In computer networks, a DMZ [4] (demilitarised zone) is a physical or logical sub-network that separates an internal local area network from other untrusted networks. Servers for clients, resources and services are located in the DMZ so that users on the internet can use them but the rest of the network (LAN) remains unreachable from the internet.

Hence in conclusion there is no universal topology that all company use and a company should choose a topology that is best suited for their need.

References

[1] http://searchnetworking.techtarget.com/tutorial/Introduction-to-firewalls-Types-of-firewalls

[2] http://www.netsentron.com/forum/how-to-choose-a-firewall/

[3] http://searchsecurity.techtarget.com/tip/Choosing-the-right-firewall-topology-Bastion-host-screened-subnet-or-dual-firewalls

[4] http://searchsecurity.techtarget.com/definition/DMZ- 