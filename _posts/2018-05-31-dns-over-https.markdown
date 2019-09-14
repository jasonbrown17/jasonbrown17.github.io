---
layout: post
title:  "DNS Over HTTPS"
categories: DNS HTTPS
---

### How does DNS work?

Protecting your privacy online is a hot topic for many. Though many websites have transitioned from HTTP to HTTPS, allowing web traffic to be secured, this does not protect your overall privacy. The internet still relies on older protocols to ensure you are accessing the right website or other online resources.

DNS, or the Domain Name Service, is one of those protocols we rely heavly on everyday. Every internet connected device has at least one IP address. DNS allows you to type in google.com and it resolves the IP address associated to it. One of the biggest issues with DNS is that it is one of those legacy protocols we rely on everyday. It has no built in security and runs completely in clear text. This allows your Internet Service Provider, or anyone capable of capturing internet traffic, to see what websites you access. This means that even if you are accessing a HTTPS website, others can still see your internet history.

### Why is this bad?

As we continue on in the digital age, our internet history is being used against us. Website cookies, internet searches, and DNS queries are being sold to marketing companies. Everything you do is being bought and sold to a number of companies and marketing firms. These companies then take this information and use targeted ads in order to get you as the consumer to purchase online goods and services. There have been steps made to discourage and even eliminate this type of intrusion into our privacy however they have not been totally adopted due to complexity.

### Protecting your online privacy

Using HTTPS over HTTP is a great first step in protecting the security and privacy of your internet traffic. The next step is to look at protecting the privacy and security of your DNS queries too. Many online DNS services provide this level anonyminity and security. CloudFlare’s 1.1.1.1 DNS over HTTPS is one such service that provides this level of protection. Their privacy policy states that under no circumstances will they ever sell your internet searches to outside third party companies. Quad9 by IBM states the same information in their privacy policy too. However just setting your DNS settings to either of these services is not enough. Your router or computer will still send clear text DNS queries without additional configurartion.

CloudFlare offers a number of different ways to protect your online searches. If you are looking to just configure the service on your local machine, instructions and downloads can be found at their Downloads page. Quad9 offers the same level of integration.

If you are looking to provide DNS over HTTPS for your entire household or business your in luck as well. There are simple ways to get this configured so that everyone can take advantage. Different types of routers, including pfSense, can be configured to run DNS over HTTPS. To do so, you can utilize Untangle and configure it to run DNS over port 853. The configuration will be placed into the custom option area and will look like this:

`
server:
forward-zone:
name: "."
forward-ssl-upstream: yes
forward-addr: 1.1.1.1@853
forward-addr: 1.0.0.1@853
forward-addr: 2606:4700:4700::1111@853
forward-addr: 2606:4700:4700::1001@853
forward-addr: 9.9.9.9@853
forward-addr: 149.112.112.112@853
`

Once that is in place, and you have saved your configuration, you will now have an additional sense of privacy and security while online.
