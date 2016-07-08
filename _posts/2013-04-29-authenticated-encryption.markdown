---
layout: post
title:  "An Introduction to Authenticated Encryption"
date:   2013-04-29 11:35:05
post_author: Shawn Fitzgerald
categories: crypto
---


Historically, independent encryption and message authentication codes (MAC) have been used to provide message confidentiality and integrity. This has led to confusion within the user community, as there was no standard construct for combining these. The result of this has been often insecure combinations that have resulted in a number of high profile system breaks such as the use of WEP in 802.11. Over the last ten years, the cryptographic community has moved to a more formal approach to the development and specification of cryptographic algorithms and modes of operation; this has resulted in provably secure Authenticated Encryption primitives that provide both confidentiality and integrity.

Authenticated Encryption is beginning to see deeper adoption in both security standards and implementations, yet is still not commonly understood by the security community.  In this paper, iSEC's Shawn Fitzgerald attempts to bridge the gap between academic and technical standards and non-technical overviews by presenting a systematic introduction to Authenticated Encryption and the most commonly used modes such as CCM, EAX, OCB and GCM.

The paper can be downloaded [here][paper-dl].


[paper-dl]: https://github.com/iSECPartners/publications/raw/master/whitepapers/introduction_to_authenticated_encryption.pdf
