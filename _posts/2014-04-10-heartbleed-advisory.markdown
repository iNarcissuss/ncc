---
layout: post
title:  "Heartbleed (CVE-2014-0160) Advisory"
date:   2014-04-10 11:00:00
post_author: Andy Grant, Justin Engler, Aaron Grattafiori
categories: advisories ssl
---

News of a major widespread vulnerability discovered by Neel Mehta came out
Monday, April 7 2014. This vulnerability allows a network attacker to read
memory from programs that use certain versions of the OpenSSL library, e.g.
web servers, VPN clients and servers, or mail transfer agents. Vulnerable data
could include:

* Certificate private keys and session keys
* Any credentials (such as username and password) sent to the endpoint.
  Session cookies and similar bearer tokens are also affected.
* The actual data that was intended to be protected (such as financial data or
  account numbers).
* Other potentially sensitive data in memory (such as memory addresses and
  their contents) that could allow an attacker to more easily exploit other
  vulnerabilities.


### <a name="versions"></a>What is vulnerable?

This vulnerability has been in source code since December 2011 and in
production OpenSSL versions since March 2012:

* OpenSSL 1.0.1 through 1.0.1f (inclusive) are vulnerable
* OpenSSL 1.0.1g is NOT vulnerable
* OpenSSL 1.0.0 branch is NOT vulnerable
* OpenSSL 0.9.8 branch is NOT vulnerable

Even if you are not directly using OpenSSL, a large number of software packages
incorporate OpenSSL and are vulnerable.

### Who is vulnerable?

Anyone who has run any product using OpenSSL versions 1.0.1 through 1.0.1f
even if you are currently patched is vulnerable. Even if your organization
does not run OpenSSL directly, it is a part of many other software packages.
Additionally, appliances such as SSL/TLS terminators, mail servers, instant
messaging servers, and VPN concentrators could be running OpenSSL internally.
This is not limited to servers either. Any client software that uses a
vulnerable version of OpenSSL can be attacked. Our investigations into the
exploitability of client software are ongoing.

### What action should be taken on the server side?

iSEC recommends performing the following discovery and remediation steps:

**Discovery:** determine if you are running a [vulnerable version](#versions)
of OpenSSL

**Fix the base issue going forward:**

* Update to OpenSSL 1.0.1g or newer, or recompile the current version in use
  with heartbeats disabled via the `–DOPENSSL_NO_HEARTBEATS` option.
* Restart all processes that load the OpenSSL library

**Mitigate potential damage:**

* Generate and deploy a new public and private key pair. 
* Revoke old, assumed-compromised private key. Check with the issuing
  Certificate Authority (CA) for details on how to revoke a compromised
  private key. You may wish to request a new certificate even before your
  production systems are fully patched so that it has a chance to age before
  deployment to minimize problems for clients with incorrect clocks.
* Invalidate all active sessions
* Encourage users to change passwords
* Elevate fraud detection procedures
* Notify vendors of any vulnerable commercial software or appliances.

Due to the severity of the impacts of an exploit, if a service cannot be
upgraded or recompiled, consider removing the service from the internet until
fixes can be applied.

### What action should be taken with client software?

Currently the most active threat is to servers, however a network attacker
could use this bug to attack clients as well. Depending on the functionality
and use of your product, client-side attacks could steal sensitive session
data, user credentials, and private keys for client certificates.

**Discovery:** determine if clients/products are using a [vulnerable
version](#versions) of OpenSSL.

**Fix the base issue going forward:**

* Update to OpenSSL 1.0.1g or newer, or recompile with heartbeats disabled
* Release update/patch

**Mitigate potential damage:**

* Notify customers
* Invalidate sessions
* Encourage users to change passwords
* Encourage users to generate new public and private key pair for client-side
  certificates
* Revoke old, assumed-compromised private key of client-side certificates
* Elevate fraud detection procedures

### What action should be taken by users/consumers?

Almost every person uses some service or software that is vulnerable to
Heartbleed. Although much of the burden resides on software vendors to provide
prompt patches, there are a few things you can do to minimize your personal
risk:

* Log out of services
* Determine if services are currently vulnerable by looking for an advisory or
  checking one of the available lists, such as [Mashable's list](http://mashable.com/2014/04/09/heartbleed-bug-websites-affected/)
* Avoid using vulnerable services and notify them that they are vulnerable
* After services are no longer vulnerable, change passwords

### More information

* CVE-2014-0160
* [http://heartbleed.com/](http://heartbleed.com/)
* [https://www.openssl.org/news/secadv_20140407.txt](https://www.openssl.org/news/secadv_20140407.txt)
* [https://www.nccgroup.com/en/blog/2014/04/heartbleed-openssl-vulnerability/](https://www.nccgroup.com/en/blog/2014/04/heartbleed-openssl-vulnerability/)
* [http://security.stackexchange.com/a/55250](http://security.stackexchange.com/a/55250) - Details on client-side attacks
