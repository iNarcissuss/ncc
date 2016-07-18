---
layout: post
title:  "Shellshock Advisory"
date:   2014-09-25 1:23:55
post_author: NCC Group
categories: advisories
---

## Executive Summary

Immediate patches are required to fix a vulnerability in bash that allows
arbitrary code execution from unauthenticated users.

The full impact of vulnerable vectors may never be enumerated, so patching is
required immediately, as in-the-wild attacks are being seen.

The vulnerability is not fully resolved by the available patch, so a second
round of patching will be required once the subsequent patch is available.

It is not necessary to restart computers or processes following patching.

## Impact & Determining Exposure

Shellshock enables code execution, arbitrary file disclosure, and system
compromise from unauthenticated remote attackers. The ways that a system could
be vulnerable to this bug are numerous, and no exhaustive list could be
compiled. However, some of the common scenarios are:

* Web servers using CGI scripts that are written in bash
* Web servers using CGI scripts that are written in other languages that
  invoke certain function calls:
   * C-based scripts calling system() or popen()
   * Python-based scripts that call os.system() or os.popen()
   * PHP-based scripts that call system() or exec() (when run in CGI mode)
   * Perl-based scripts that invoke shell commands
* Restricted SSH shells using ForceCommand can be bypassed. Some git and
  subversion deployments use such restricted shells.
* If an attacker is in a position to forge DHCP responses, it can enable
  root-level code execution in DHCP clients
* Set-UID applications may allow local escalation to root
* CUPS-based printer daemons are likely to be affected
* Mac and Linux Desktops are affected, and are likely to allow privilege
  escalation to a root user

Certain common deployments are not affected:

* Regular use of SSH is not affected as users already have shell access
* PHP scripts that use mod\_php are not affected, nor is mod\_python or mod\_perl
* Sudo by itself is not affected

Finally, there is no need to restart services after patching. Running
processes have passed the window of vulnerability and new processes will be
running the new, patched code.

## Patching

Linux Operating Systems have deployed patches:

* RHEL: [https://rhn.redhat.com/errata/RHSA-2014-1293.html](https://rhn.redhat.com/errata/RHSA-2014-1293.html)
* Ubuntu: [http://www.ubuntu.com/usn/usn-2362-1/](http://www.ubuntu.com/usn/usn-2362-1/)
* Debian: [https://lists.debian.org/debian-security-announce/2014/msg00220.html](https://lists.debian.org/debian-security-announce/2014/msg00220.html)
* CentOS: [http://centosnow.blogspot.com/2014/09/critical-bash-updates-for-centos-5.html](http://centosnow.blogspot.com/2014/09/critical-bash-updates-for-centos-5.html)
* Gentoo: An updated bash package is available in portage
* OpenSUSE: [http://support.novell.com/security/cve/CVE-2014-6271.html](http://support.novell.com/security/cve/CVE-2014-6271.html)

Mac OS X is not yet patched, but manual instructions to recompile bash from source are available at: [https://apple.stackexchange.com/questions/146849/](https://apple.stackexchange.com/questions/146849/)

## An Imperfect Fix

Unfortunately, the patch supplied is incomplete. As [noted by Tavis
Ormandy](https://bugzilla.redhat.com/show_bug.cgi?id=1141597#c23), other
vectors still exist to bypass protections and perform invalid actions, such as
overwriting files. There are also indications that there are [memory corruption flaws](http://www.openwall.com/lists/oss-security/2014/09/25/32) as well. While no one has publicly demonstrated code execution for
these unpatched bypasses, it seems likely to be possible. A second CVE (CVE-2014-7169) has
been created to track this issue.

Red Hat has an experimental mitigation that requires many manual steps to use
available at: [https://access.redhat.com/articles/1200223](https://access.redhat.com/articles/1200223)

Red Hat and NCC both advise deploying the available patch immediately and
being prepared to deploy a second patch, when one becomes stable and tested
shortly.

## In the Wild Attacks

Shellshock is being actively scanned for and exploited on the Internet
at-large currently.

Robert Graham is one security researcher who has [initiated an Internet-wide
scan](http://blog.erratasec.com/2014/09/bash-shellshock-scan-of-internet.html#.VCQXQitdVH0)
from the IP address 209.126.230.72. His scan, and many others, use a ping
command to call back to a server, alerting them that your server is vulnerable
– although this is not the only mechanism one could use.

Besides internet scans, several Metasploit modules are available, and a few exploits have been posted online. These include exploits that [provide shell access to a server](http://pastebin.com/raw.php?i=166f8Rjx), read [arbitrary files the web server has access to read](https://www.invisiblethreat.ca/2014/09/cve-2014-6271/), targeting [DHCP clients](https://www.trustedsec.com/september-2014/shellshock-dhcp-rce-proof-concept/), and a report of a [payload that exploits](https://gist.github.com/anonymous/929d622f3b36b00c0be1) a [kernel vulnerability](http://www.kernelmode.info/forum/viewtopic.php?f=16&t=3505).  The kernel exploit is not yet confirmed to exploit a previously known or unknown vulnerability.

## IDS Signatures and Detection

IDS vendors are producing rules that will attempt to detect and block
attempted exploitation of this issue. Rules are available for:

* mod\_security: [https://access.redhat.com/articles/1200223](https://access.redhat.com/articles/1200223)
* iptables: [https://access.redhat.com/articles/1200223](https://access.redhat.com/articles/1200223)
* Snort: [http://www.volexity.com/blog/?p=19](http://www.volexity.com/blog/?p=19)
* Suricata: [http://www.volexity.com/blog/?p=19](http://www.volexity.com/blog/?p=19)
* Akamai has rules deployed in its WAF products: [https://blogs.akamai.com/2014/09/environment-bashing.html](https://blogs.akamai.com/2014/09/environment-bashing.html)
* CloudFlare has similarly deployed rules in its WAF Products: [https://blog.cloudflare.com/bash-vulnerability-cve-2014-6271-patched/](https://blog.cloudflare.com/bash-vulnerability-cve-2014-6271-patched/)

## Technical Details of the Flaw

The vulnerability was discovered by Stephane Chazelas and can be tested for
manually using the following command:

    env x='() { :;}; echo vulnerable' bash -c "echo this is a test"

If it outputs ‘vulnerable’, the system is vulnerable.  This bug arises because
of an unusual feature of bash that allows exporting functions as well as
environment variables. This feature is specific to bash, and no other shells
are known to be vulnerable. (However, on some systems, other shells will
actually be symlinks to bash.)

The actual vulnerability is in the parser for these exported functions. It
does not parse the function correctly, and upon invocation will automatically
execute trailing code defined after the function.

Any variable beginning with "() {" is automatically treated as a function –
but the aspect that makes this bug so prevalent is that environment variables
are populated in unexpected places from user input.  For example, environment
variables like HTTP\_COOKIE and HTTP\_USER\_AGENT are often populated for CGI
scripts. And PHP, Perl, Python, and other scripts are often run as CGI scripts
under a web server.

This results in a perfect storm of unexpected vectors of automatic remote code execution, most commonly on web servers. For more details, a good technical blog post is: [http://lcamtuf.blogspot.co.uk/2014/09/quick-notes-about-bash-bug-its-impact.html](http://lcamtuf.blogspot.co.uk/2014/09/quick-notes-about-bash-bug-its-impact.html)

## References

* [https://bugzilla.redhat.com/show_bug.cgi?id=1141597#c23](https://bugzilla.redhat.com/show_bug.cgi?id=1141597#c23)
* [http://blog.erratasec.com/2014/09/bash-shellshock-scan-of-internet.html#.VCQXQitdVH0](http://blog.erratasec.com/2014/09/bash-shellshock-scan-of-internet.html#.VCQXQitdVH0)
* [http://pastebin.com/raw.php?i=166f8Rjx](http://pastebin.com/raw.php?i=166f8Rjx)
* [https://www.invisiblethreat.ca/2014/09/cve-2014-6271/](https://www.invisiblethreat.ca/2014/09/cve-2014-6271/)
* [http://www.kernelmode.info/forum/viewtopic.php?f=16&t=3505](http://www.kernelmode.info/forum/viewtopic.php?f=16&t=3505)
* [https://gist.github.com/anonymous/929d622f3b36b00c0be1](https://gist.github.com/anonymous/929d622f3b36b00c0be1)
* [https://access.redhat.com/articles/1200223](https://access.redhat.com/articles/1200223)
* [http://lcamtuf.blogspot.co.uk/2014/09/quick-notes-about-bash-bug-its-impact.html](http://lcamtuf.blogspot.co.uk/2014/09/quick-notes-about-bash-bug-its-impact.html)
* [http://www.volexity.com/blog/?p=19](http://www.volexity.com/blog/?p=19)
* [http://www.troyhunt.com/2014/09/everything-you-need-to-know-about.html?m=1](http://www.troyhunt.com/2014/09/everything-you-need-to-know-about.html?m=1)
* [http://seclists.org/oss-sec/2014/q3/650](http://seclists.org/oss-sec/2014/q3/650)
* [https://blog.cloudflare.com/bash-vulnerability-cve-2014-6271-patched/](https://blog.cloudflare.com/bash-vulnerability-cve-2014-6271-patched/)
* [https://blogs.akamai.com/2014/09/environment-bashing.html](https://blogs.akamai.com/2014/09/environment-bashing.html)
* [https://apple.stackexchange.com/questions/146849/how-do-i-recompile-bash-to-avoid-the-remote-exploit-cve-2014-6271-and-cve-2014-7](https://apple.stackexchange.com/questions/146849/how-do-i-recompile-bash-to-avoid-the-remote-exploit-cve-2014-6271-and-cve-2014-7)
* [https://access.redhat.com/security/cve/CVE-2014-7169](https://access.redhat.com/security/cve/CVE-2014-7169)
* [https://access.redhat.com/security/cve/CVE-2014-6271](https://access.redhat.com/security/cve/CVE-2014-6271)
* [https://securityblog.redhat.com/2014/09/24/bash-specially-crafted-environment-variables-code-injection-attack/](https://securityblog.redhat.com/2014/09/24/bash-specially-crafted-environment-variables-code-injection-attack/)
