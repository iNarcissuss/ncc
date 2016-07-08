---
layout: post
title:  "Amazon AWS Sig V4 Burp Plugin"
date:   2013-12-10 16:30:00
post_author: Mike Warner
categories: tools
---

### Amazon AWS Sig V4 Burp Plugin

Testing Amazon Web Service APIs can be a frustrating experience for any
security researcher; each AWS web request is digitally signed with Amazon’s
publicly documented signing algorithm, making tampering with requests rather
painful. This signing algorithm has been implemented as a Burp Proxy plugin
making it easy to modify requests. Now any signed HTTP header and POST message
can be modified without the need to manually calculate the signature, allowing
time to be spent on testing rather than re-implementing a signing algorithm.

#### Benefits

* Each request is tested to determine if the signature is needed or not
* Change AWS credentials without having to reload the plugin

The [Burp Plugin](https://github.com/iSECPartners/AWS-SigV4-Signer) is hosted
on GitHub.
