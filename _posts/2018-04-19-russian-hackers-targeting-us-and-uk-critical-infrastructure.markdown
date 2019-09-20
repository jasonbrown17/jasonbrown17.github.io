---
layout: post
title:  "Russian Hackers Targeting US and UK Critical Infrastructure"
categories: Security
featured_image: '/images/blog/russia.jpg'
---

![Vladimir Putin](/images/blog/russia.jpg)

Over the last few weeks, Russian hackers have coordinated attacks against personal, government, corporations, and Internet Service Providers. These attacks are currently being directed toward IoT devices, home based modems, and corporate routers, switches and firewalls. This is in an attempt to create an organized attack against the US and UK and potentially bring down critical infrastructure.

There are a couple of reasons why these attacks are occurring against these two countries. First, the exile of diplomats from Russian embassy’s after a Russian spy was poisoned in the UK. Second, in early April, hackers went after Russian network equipment using a known Cisco configuration tool that was exposed to the public Internet. Once hackers had access to the network equipment, they were able to not only delete the configurations, but the hackers also left behind a message saying, “Don’t mess with our elections” and a picture of the American flag.

There are simple changes that you can make to your company infrastructure, even your home equipment, to safeguard assets that you own.

* Change default passwords – The default username and password on most Cisco equipment is cisco/cisco. This credential provides administrative access to the router or switch and must be changed prior to placing the device into production. Changing the default password on all equipment should be the very first thing you do.
* Maintain system level updates – Ensure that you are patching your network equipment at least quarterly if not sooner depending on the types of known vulnerabilities. The Cisco configuration tool that was used to hack into the Russian routers, had a known vulnerability.  
* Place access lists on management interfaces – There is no reason to have a way to log into a piece of equipment from anywhere in the world. There are ways of placing firewall rules on network equipment to only allow authentication attempts from known trusted networks.  
* Replace end of life/end of support equipment – High end network equipment can cost hundreds of thousands of dollars. Ensure that your organization is budgeting for replacement of aging devices so that you can continue to apply patches to your network and security equipment. A breach of information, or a complete network outage, could have significantly higher costs to fix the issues due to downtime than it would have if you purchased newer equipment with support and maintenance.  
* Stop using clear text protocols – Most legacy equipment only support Telnet or clear text web traffic. This equipment should either be pulled out of production and placed into a lab, or discarded altogether. It is a requirement nowadays to use encryption for all remote administration and even network monitoring protocols such as SNMP. If you cannot remove the equipment out of production, it is recommended that a project plan is in place to replace older legacy equipment. If replacement cannot be performed in a timely manner, the use of compensating controls such as authenticating from known trusted networks to creating an out-of-band management network is advisable.  

There are definitely some quick wins that you can put in place to better protect your network equipment from being attacked, whereas others may take a while to implement due to budget constraints. In either case, these tips will help create a heightened layer of security for your overall network equipment.
