---
layout: post
title:  "Perfect Forward Security Whitepaper"
date:   2014-09-04 11:25:55
post_author: Pratik Guha Sarkar
categories: whitepapers
---

Encrypted communication channels were created so nobody could read confidential communications - this means not only during the conversation, but also any time after it. But adversaries have the ability to monitor, record, and attack communication retroactively. Disclosure of state sponsored monitoring of electronic communications and the threat of retroactive decryption of traffic of millions of people has created an urge for an extra layer of security and privacy for all electronic communications.

iSEC has [published a whitepaper](https://github.com/iSECPartners/publications/blob/master/whitepapers/perfect_forward_security.pdf?raw=true) that looks into how Forward Security can be used to protect online communication - but covering much more than just TLS. Besides explaining the groundwork, we also explore the difference between Forward Security and Perfect Forward Security and mechanisms outside any specific implementation, modeling a generic protocol and building it up showing how Forward Security can be achieved. And on the implementation level, we also cover how to enable Forward Security in protocols you have deployed in your network today - giving a simple explanation, real life applications, advantages, and implementation in protocols like Off-the-Record (OTR) Messaging, Secure Shell (SSH), Wireless Protected Access II Protocol (WPA2-EAP-PWD), Virtual Private Networks (VPN), and of course TLS.

