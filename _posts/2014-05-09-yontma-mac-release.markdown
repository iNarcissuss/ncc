---
layout: post
title:  "Tool Release: You'll Never (Ever) Take Me Alive!"
date:   2014-05-09 11:25:55
post_author: Tom Ritter
categories: news tools
---

[A year ago](https://isecpartners.github.io/tools/2013/03/18/yontma-release.html), we released [You'll Never Take Me Alive](https://github.com/iSECPartners/yontma) — a tool that helps protects Full Disk Encrypted Windows computers from DMA and cold boot attacks.

YoNTMA runs as a background service and begins monitoring your computer any
time the screen is locked. If the power cable or Ethernet cable is
disconnected from the system while your laptop is locked, YoNTMA will
immediately hibernate the machine to ensure that the disk encryption keys do
not remain in RAM. This ensures that if a thief walks off with your powered-on
laptop, your encrypted data stays protected.

It's been a great tool that I've used happily, but when I got a new Macintosh, I ran up against [Issue #3](https://github.com/iSECPartners/yontma/issues/3) — there's no Mac version! Until today. We're releasing a new version of [YoNTMA for Macs](https://github.com/iSECPartners/yontma-mac). The source is still open and the .dmg can be downloaded from [Github](https://github.com/iSECPartners/yontma-mac/releases/download/0.9.9/yontma-0.9.9.dmg). Due to some tricks of how Macintoshes hibernate, you'll need to provide your administrative password (just once) to update the power management settings to enable a secure hibernation. Or, if you're paranoid, you can run those commands yourself and re-launch the app — don't worry, you won't hurt my feelings.

The only issue we're aware of is a [lingering issue in OS 10.9](https://discussions.apple.com/thread/5468637?start=0&tstart=0); that said, while I've experienced this issue in the past, I'm currently running 10.9 and haven't had issues in the past few months. Feel free to test and if you have problems, [open an issue on Github](https://github.com/iSECPartners/yontma-mac/issues).
