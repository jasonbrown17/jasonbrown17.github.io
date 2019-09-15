---
layout: post
title:  "Creating a Blackhole DNS with Bind 9"
categories: DNS
featured_image: '/images/blog/bind9.png'
---

![](/images/blog/bind9.png)

Malware can be delivered many different ways from either advertisements (remember the NY Times malicous ads?) to hacked websites that contain malicious code.  One technique designed to help curb these infections is through the use of DNS blackhole.  This technique will redirect your internal users to an internal website to block their access.  To do so, first install Bind on your Linux server.  Then edit your named.conf file which should be located in /etc/bind and enter:

`include ""/etc/named/blackhole.conf";`

Create a new file called blackhole.conf.  This file will contain every website you wish to redirect to an internal site, effectivly blocking your users from accessing it:

`zone "doubleclick.com" {type master; file "/etc/bind/blackhole.db";};`

Each additional website that you want to block should containt he same format as the one stated above.

Next, create your zone file which will redirect all traffic destined to FQDN’s listed in the blackhole.db file to your internal website:

##### $TTL 3600
##### @ IN SOA ns1.example.com. root.example.com. (
##### 20131020 ;
##### 3600  ;
##### 600  ;
##### 86400  ;
##### 600 )

##### @ IN NS ns1.example.com.

##### * IN A 192.168.2.254

There are plenty of websites on the Internet that maintain an updated list of malware websites.  One that I use quite frequently is Malware Domain List
