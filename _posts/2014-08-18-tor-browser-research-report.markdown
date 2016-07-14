---
layout: post
title:  "Tor Browser Research Report Released"
date:   2014-08-13 11:25:55
post_author: Tom Ritter, Andy Grant
categories: news whitepapers
download_name: Whitepaper
download_link: https://github.com/iSECPartners/publications/tree/master/reports/Tor%20Browser%20Bundle
related: ["2013/10/14/open-tech-fund-report-release"]
---

As part of our [work with the Open Technology
Fund](https://isecpartners.github.io/2013/10/14/open-tech-fund-report-release.html),
we recently worked with the [Tor Project](https://www.torproject.org/) to see
how Tor Browser stands up in terms of modern exploit mitigations, and what
could be done to make it harder to develop exploits for.

Tor Browser is based on Firefox, so it inherits the strengths and weaknesses
of Firefox — but one of the things Tor Project is working on is a [security
slider](https://trac.torproject.org/projects/tor/ticket/9387) that will let
people disable features of the browser depending on their security posture.
If you're extra paranoid you'll ratchet it all the way up and disable
Javascript; if you're less paranoid, you can put it on 'Low' and disable
things like obscure font rendering features only used in South East Asia.

Tor Project has [published a blog
post](https://blog.torproject.org/blog/isec-partners-conducts-tor-browser-hardening-study)
that summarizes the report from their point of view and links to a number of
issues on their bugtracker and other documentation.

This project was more of a research engagement than a security assessment — a
lot of this engagement was identifying features that should be placed on the
slider, and making recommendations for where they should land.  But we looked
at a lot of other more general hardening items too.  We checked the status of
DEP and ASLR on Windows and Mac, and found an interesting lack of exception
handling on the Windows build, due to the MinGW build process (this throws
SafeSEH and SEHOP out the window). We also went through, with the cooperation
of the Mozilla Security team, and categorized over a hundred past security
vulnerabilities in Firefox into feature category and bug type (Use-After-Free
wins the latter overwhelmingly.) We analyzed a few public and private
exploits, and also investigated enabling assertions in certain classes in
Firefox. We have a skeleton patch for the latter, but it's more a proof of
concept than something we think they should use. One of the other major items
was looking at replacing Firefox's memory allocator (jemalloc) with a more
hardened allocator (PartitionAlloc from Chrome). Fortunately, Mozilla makes
this pretty easy, so most of the work is in adapting PartitionAlloc and making
full use of its partition features.  There are several other parts to the
report, including looking at protocol handlers, media formats, and making
regression tests for DOM object exposure.

We had a ton of fun working on this project and we'd like to thank Mike Perry
at Tor for working with us so closely, OTF for sponsoring the work, and all
the people inside iSEC and the security community we talked about this project
with who gave us ideas — especially Chris Evans from Google (the author of
PartitionAlloc). The report clocks in at about 30 pages, but with the
appendices (which have patch files), it balloons up to a whopping 150 pages.
You can find the report, and all the patch files [in our publications
repository](https://github.com/iSECPartners/publications/tree/master/reports/Tor%20Browser%20Bundle).

