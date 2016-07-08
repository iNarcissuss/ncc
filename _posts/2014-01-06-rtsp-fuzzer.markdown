---
layout: post
title:  "Announcing the Release of RtspFuzzer"
date:   2014-01-07 12:13:00
post_author: Michael Lynch
categories: tools fuzzing
---

iSEC Partners is pleased to announce the release of RtspFuzzer, an open-source fuzzer for the real-time streaming protocol (RTSP). RTSP is a text-based protocol that facilitates media streaming. We have been developing this fuzzer over the past several months as we fuzz different media players. Though this protocol doesn't receive much attention, most popular media players implement it and these implementations have previously been a source of critical security vulnerabilities (including [QuickTime](http://cvedetails.com/cve/2007-6166) and [Windows Media Player](http://www.cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2010-3225)).

Using RtspFuzzer, we [uncovered a new, critical vulnerability](https://isecpartners.github.io/fuzzing/vulnerabilities/2013/12/30/vlc-vulnerability.html) in the Live555 library, an open-source implementation of the RTSP protocol that several media players and servers use, including VLC. The vulnerability allowed an attacker to gain remote code execution on a victim's system if they could induce a VLC user to visit a malicious web page or open a malicious playlist file.

### Using RtspFuzzer

See the Github repository page to download the tool and for quick start instructions:

[https://github.com/iSECPartners/RtspFuzzer](https://github.com/iSECPartners/RtspFuzzer)

We created the fuzzer using the [Peach fuzzing framework](http://www.peachfuzzer.com). RtspFuzzer has built-in configurations for Windows binaries of QuickTime, VLC, and openRTSP, but users can easily adjust the configuration and use this fuzzer to test any RTSP client on any Peach-compatible platform.

### Advice for developing fuzzers with Peach

Creating RtspFuzzer was a great way to learn to use Peach. Peach is a very powerful framework for fuzzing, but many people shy away from it and instead create one-off fuzzers because they perceive Peach's learning curve as too steep. Peach does indeed take some time to learn, but it does also save you from rolling your own implementation of a lot of things that Peach does for you, such as integrating with debuggers, mutating your data to match common attack patterns, or logging results in an organized way.

I would like to see Peach succeed because, despite its current problems, Peach makes it easy to write fuzzers that others can reuse and adapt. As more people use Peach, more information about its use will be available and this will reduce the learning curve. The Peach development team is [very responsive](http://forums.peachfuzzer.com/forumdisplay.php?2-Peach-3-Beta), and as the user base increases, more people will be able to report bugs and feature suggestions. If you're thinking of writing a fuzzer with Peach, keep the following tips in mind:

* **Treat your Peach pit like a regular program.** Keep it under source control and use bug tracking to maintain a list of issues in your fuzzer. Debugging your fuzzer will be a *lot* easier if you can revert to a known good state.
* **Expect bugs in Peach.** While Peach has existed since 2004, the latest 3.x version is a complete rewrite of the product in .NET and was first released in May, 2013. Peach works well for the most part, but there are definitely some rough edges, especially as your pits get more complex. You need to account for this in planning if you're building your fuzzer on a schedule. I recommend building Peach from source so that if you suspect you've run into a bug in the framework itself, you can debug it more easily.
* **Fuzz early and fuzz often.** When I started working on the RTSP fuzzer, my first task was to define the RTSP protocol as precisely as I could in Peach. What I *wish* I had done first was build a mostly dumb fuzzer that spoke just enough RTSP to do basic fuzzing of a test application such as VLC, then build up from there. Seeing how Peach works and how it interprets the data in pit files is immensely helpful in designing your fuzzer. Look at the kind of data that Peach generates and see if anything is causing iterations to run slowly or to stop.

