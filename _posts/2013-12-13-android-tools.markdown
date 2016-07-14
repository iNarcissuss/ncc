---
layout: post
title:  "SSL pinning bypass and other Android tools"
date:   2013-12-13 14:42:42
post_author: Marc Blanchou
categories: android
github_names: ["Android SSL Trustkiller", "Android KillPermAndSigChecks", "Android OpenDebug"]
github_links: ["https://github.com/iSECPartners/Android-SSL-TrustKiller", "https://github.com/iSECPartners/Android-KillPermAndSigChecks", "https://github.com/iSECPartners/Android-OpenDebug"]
---

iSEC is releasing several [Cydia Substrate][cydia-url] extensions to
facilitate the black box testing of Android applications:

#### Android-SSL-TrustKiller

This tool hooks various methods in order to disable SSL certificate pinning,
by forcing the Android application to accept any SSL certificate. Once
installed, it works across all applications on a device. See the [project
page][trustkiller].

#### Android-KillPermAndSigChecks

This tool disables signature and permission checks for Android IPCs. This can
be useful to test internal or restricted IPCs in specific cases/scenarios. See
the [project page][KillPermAndSigChecks].


#### Android-OpenDebug

This extension makes all applications running on the device debuggable; once
installed, any application will accept a debugger to attach to them. We
originally wrote a different version that hooked on the
android.content.pm.PackageParser class; however, MWR released a new technique
last week involving a faster way to do it, which is what this Cydia Extension
now uses. See the [project page][Android-OpenDebug].


[Android-OpenDebug]: https://github.com/iSECPartners/Android-OpenDebug
[KillPermAndSigChecks]: https://github.com/iSECPartners/Android-KillPermAndSigChecks
[trustkiller]: https://github.com/iSECPartners/Android-SSL-TrustKiller
[cydia-url]: http://www.cydiasubstrate.com/
