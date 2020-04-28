---
layout: post
description: "How to architect ISC BIND within an organizaion"
title:  "DNS Architecture"
categories: Privacy DNS Malware URL Web Filtering 
date: "2020-04-07 00:00:00 -0400"
featured_image: "/images/blog/dns2.jpg"
---

![DNS Architecture](/images/blog/dns2.jpg)

Deploying a local [BIND][iscbind] server for an organization can be quite daunting. There are a multitude of options available within the configuration of the service. Though secure configurations are extremely important, one must not overlook how to architect its set up within a network. Architecting the service correctly from the start will ease configuration headaches further down the road.

### Network Segmentation

Network segmentation must be considered when standing up new systems. Segmentation is performed through the use of a firewall or proxy device which restricts network traffic. This restriction provides necessities by blocking unused protocols, access to network ports, and access from systems and services outside of the segment. 

To segment services properly, an organization can either segment individual systems from each other or by creating a [Community Of Interest (COI)][coi]. A COI is the combination of like systems within a network segment. For example, a DNS COI is the creation of a network segment where all of the organization's DNS servers reside. Though this is not as secure as segmenting each DNS server away from each other, this is more secure than placing all systems within the same, flat, network segment. Architectural diagram is shown below:

![Hidden Primary](/images/blog/hidden_primary.jpg)

### Primary DNS

When deploying any DNS service, whether it is BIND or a different system, the primary DNS server must be as secure as possible. The primary server is the source of all your DNS naming information. If someone were to gain access to this server, or if the system is misconfigured, they would have the possibility to change DNS records which would allow the attacker to redirect users to phishing sites. This is why an organization must deploy two or more secondary servers.

### Hidden Primary

In a hidden primary configuration, the primary DNS server is never exposed to anyone. The organization configures its DHCP server to advertise the secondaries and not the primary. Firewall rules restrict DNS traffic to only the secondary servers and disallow anyone from accessing the server outside of the IT department. This is to limit the exposure of the primary server. By not advertising the primary server, it further reduces the amount of information gathered by a potential attacker.

### Secondary DNS

As the primary server is never advertised to the users, or the public, the secondary servers are exposed. These servers receive naming information from the primary server and are configured to allow lookups. Firewalls or DNS proxies must be configured to only allow DNS traffic to traverse the network and limit the number of requests, preventing certain types of attacks.

The hidden master architectural concept is not something new, however it is not well known. By limiting the exposure of the master server, allowing users to only access the secondaries, prevents a number of attacks an organization could face. This is an important initial step when planning for an initial DNS deployment, or redeployment, of the service. Getting this right starting out will help secure the rest of the configuration down the road.

[iscbind]: https://www.isc.org/bind/
[coi]: https://en.wikipedia.org/wiki/Community_of_interest_(computer_security)