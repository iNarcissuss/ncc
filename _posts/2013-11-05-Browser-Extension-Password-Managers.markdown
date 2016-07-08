---
layout: post
title:  "Browser Extension Password Managers"
date:   2013-11-05 17:45:55
post_author: Paul Youn
categories: whitepapers passwords
---


Advancements in password cracking and frequent theft of password databases
endanger single-factor password authentication systems. Password managers
are one of the only tools available that can help users remember unique
high-entropy passwords, and other secrets such as credit card numbers, for
a large number of applications. Can password managers deliver on security
promises, or do they introduce their own security vulnerabilities? This
paper examines popular browser-based password managers and presents common
security flaws that could be exploited to remotely extract a user's
password.

Previous research on password managers has focused on the cryptographic
protections of the passwords themselves in particular environments such as
[mobile devices](http://media.blackhat.com/bh-eu-12/Belenko/bh-eu-12-Belenko-Password_Encryption-Slides.pdf).
This research instead focuses on browser specific integrations and mechanisms
to remotely compromise credentials. Four of the
most popular password managers were examined: LastPass, OneLastPass, 1Password, and MaskMe.

This research shows that the examined password managers made design decisions
that greatly increase the chance of users unknowingly exposing their passwords
through application-level flaws. Many of the flaws relate to the
browser-integrated password managers that don't follow the same-origin policy
that is crucial to browser security. In the case of password managers, this
means that passwords could be filled into unintended credential forms, making
password theft easier.

Check out the full paper
[here](https://github.com/iSECPartners/publications/blob/master/whitepapers/password_managers.pdf?raw=true).
