---
layout: post
title:  "Redirecting traffic with dnsRedir.py"
date:   2013-09-05 15:54:55
post_author: Tim Newsham
categories: tools
github_name: dnsRedir
github_link: https://github.com/iSECPartners/dnsRedir
---


Often while performing network protocol testing, we want to be able to redirect traffic going to a legitimate server to a server of our own. If the program in question is on the local machine and uses standard name resolution, it's quite simple to edit the /etc/hosts file. However, this is not always the case. In these situations, it's convenient to have a DNS server that provides an intentionally incorrect answer to DNS lookups. Setting up a DNS server can be a pain, and then there's the matter of wanting to allow most queries to complete normally without interference.

DnsRedir is a small tool built to address this need. It implements a small DNS server in Python that can answer a select few queries with intentionally false data while proxying all other queries through to a real DNS server. It is implemented to be small and easy to carry around. It should work fine in Windows, Linux and OS X, and its only depedency is that a recent version of Python 2.* be installed.

### Getting the tool

See the [Github repository page](https://github.com/iSECPartners/dnsRedir) for documentation and to download the tool.
