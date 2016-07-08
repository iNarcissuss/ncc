---
layout: post
title:  "ZigTools: An Open Source 802.15.4 Framework"
date:   2014-08-04 08:30:00
post_author: Mike Warner
categories: tools
---

ZigTools is a Python framework, which was developed to reduce the complexity in writing additional functionality in communicating with a Freakduino (a low cost Arduino based 802.15.4 platform). Features such as initializing the radio, changing channels, sniffing network traffic, sending raw data and processing that data can be written in just a few lines. This allows developers to focus on writing more complex and feature rich applications without worrying about low level communications between the radio and system.

#### Benefits

* Sniffed data is saved in a pcap format, which can later be dissected by popular applications
* Replay packets directly from pcap file
* All aspects of the packet can be modified, allowing developers to test Layer 2 and 3 functionality of 802.15.4 and Zigbee systems

iSEC Partners is pleased to publicly release this version of the [ZigTools](https://github.com/iSECPartners/ZigTools) framework at [Black Hat USA 2014 Arsenal](https://www.blackhat.com/us-14/arsenal.html#Warner), a tools/demos area.
