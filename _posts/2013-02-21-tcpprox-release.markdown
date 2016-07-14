---
layout: post
title:  "Tool Release: tcpprox"
date:   2013-02-21 11:35:05
post_author: Tim Newsham
categories: tools
github_name: tcpprox
github_link: https://github.com/iSECPartners/tcpprox
---


_Tcpprox_ is a simple command line tcp proxy written in Python. It is designed to have very minimal requirements - it runs directly from Python (tested in Python 2.7) from a single source file (unless the auto-certificate option is used).

When running, the proxy accepts incoming TCP connections and copies data to a TCP connection to another machine. Options allow for SSL and IPv6 connections and for the logging of all data. Data is logged in a format that preserves connection, timing and direction information and a small utility is provided to dump out the information in various formats. A small utility is also provided for generating CA and SSL certificates. This utility is the only component that relies on an external python library, but it can be run on a different machine if necessary.

In comparison with other TCP proxy tools, _tcpprox_ is:

* simpler.
* built to support both IPv6 and IPv4.
* able to auto-generate SSL certificates.
* capable of extensive logging in different formats.


### Project Page

Check it out on _tcpprox_'s [Github page][tcpprox-gh].


[tcpprox-gh]: https://github.com/iSECPartners/tcpprox