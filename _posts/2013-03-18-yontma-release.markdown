---
layout: post
title:  "Tool Release: YoNTMA"
date:   2013-03-18 11:35:05
post_author: Michael Lynch
categories: tools
---

You're a responsible defender of your data. You keep all of your disks encrypted. You hibernate your laptop when you're not using it to keep any sensitive data out of RAM. You're known by friends, family, and colleagues as a tireless crusader against data theft. But do you hibernate your laptop when you visit a co-worker's office for a few minutes? What about when you get up to use the bathroom? What happens if a thief snatches your laptop while it's locked, but still powered on? The encryption keys are still in memory, which makes them vulnerable to DMA or cold boot attacks. Once the thief has the data encryption keys, they effectively have physical access to an unencrypted laptop, which means game over for your data. 


### You'll Never Take Me Alive!

Enter _YoNTMA_! _YoNTMA_ (You'll Never Take Me Alive!) is a tool designed to enhance the protection of encrypted data. _YoNTMA_ runs as a background service and begins monitoring your computer any time the screen is locked. If the power cable or Ethernet cable is disconnected from the system while your laptop is locked, _YoNTMA_ will immediately hibernate the machine to ensure that the disk encryption keys do not remain in RAM. This ensures that if a thief walks off with your powered-on laptop, your encrypted data stays protected.


### Project Page

iSEC Partners is pleased to announce the first public release of _YoNTMA_. The project is hosted on [GitHub][yontma-gh].
Try it out and let us know what features you'd like to see or any other feedback you have on the [Issues][yontma-issues] page.

[yontma-gh]: https://github.com/iSECPartners/yontma
[yontma-issues]: https://github.com/iSECPartners/yontma/issues
