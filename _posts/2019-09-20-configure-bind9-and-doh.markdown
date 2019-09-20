---
layout: post
title:  "Bind9 and DNS-over-HTTPS"
categories: Privacy DNS HTTPS TLS
featured_image: '/images/blog/dns.jpg'
---

![](/images/blog/dns.jpg)

Privacy and security professionals have been pushing for encryption of internet traffic for many years now. Not only has there been a significant push from the privacy community, search engine giants like Google almost force websites to use encryption to increase search engine optimization (SEO) to drive higher results. Though the costs of purchasing Transport Layer Encryption (TLS) can be quite expensive, open source projects such as [Let’s Encrypt][letsenc] allow anyone to create a publicly acceptable TLS certificate for free. These certificates are accepted by major browsers, without throwing warnings, and protects the privacy of the user accessing the site. This only resolves half of the problem.

In a recent [article][eff-article] released by the [Electronic Frontier Foundation (EFF)][eff], DNS is one of the biggest internet privacy issues facing home and corporate users. In its current implementation, DNS relays queries in clear text. This allows Internet Service Providers (ISP’s), or anyone inline of your internet traffic, to look at DNS queries and begin to build a profile on you.

### Why is this a problem?

Prior to accessing a website, regardless whether or not it uses encryption, your computer performs a DNS lookup to find the IP address of the website you are trying to access. For instance, a simple DNS request to look up where [cnn.com][cnn] resides goes out over plain text for anyone to see. Then once the computer knows the IP address it is supposed to be access, the web browser makes a request to the website over a TLS connection.

A person sniffing the traffic may not at that point know the contents of the website you are looking at, the individual however does know that you accessed [cnn.com][cnn]. As you might imagine, this is a significant privacy issue where an ISP or the like can then build a profile on you and sell it to third party marketers which can then target ads.

### Solving it on the individual level

There are plenty of tools out there that individuals can use to protect their internet traffic. From applications which can be loaded on a computer or smart device to the use of VPN’s and Tor, these can all protect a specific person. What if you wanted to protect a household or an organization? Use of individual applications would be cumbersome to have everyone use individual applications.

### Bind9 with DNS-over-HTTPS

One such was to do this is to set up a Bind DNS server. This will allow everyone in the organization to perform DNS queries and have those queries safeguarded from data mining. However this still allows someone to sniff DNS queries as they are sent in clear text. To overcome this problem we need to install [‘cloudflared’][cloudflared] on the server. The cloudflared service will then perform DNS-over-HTTPS queries, encrypting your internet traffic from the Bind server to Cloudflare’s DNS resolvers. This prevents anyone from sniffing your DNS traffic, allowing for additional anonymity on the internet.

### Getting your system ready

First you will need to install and configure Bind on your server. Once that is complete, download and install the [cloudflared][cloudflared] application on the server. After installation you will need to make one minor change to the forwarders section in your `named.conf.options` file. First, remove the comments in front of forwarders, these will be in the form of double forward slashes - //
Next, add the port number to the loopback IP address. The configuration will then look like:

`forwarders { 127.0.0.1 port 54; };`  

After that, load up Wireshark and take a look at the traffic. You should no longer see the DNS protocol being used as everything will be running over TLS.

### Am I now fully protected?

No. Though you are one step closer, you still need to ensure that you are performing your due diligence when accessing websites on the internet. Be careful when accessing websites that do not use encryption, especially when typing in your username and password. Use multifactor authentication in addition to a password manager and always double check the website you are accessing.




[letsenc]: https://letsencrypt.org
[eff-article]: https://www.eff.org/deeplinks/2019/09/encrypted-dns-could-help-close-biggest-privacy-gap-internet-why-are-some-groups
[eff]: https://eff.org
[cnn]: https://cnn.com
[cloudflared]: https://developers.cloudflare.com/argo-tunnel/downloads/
