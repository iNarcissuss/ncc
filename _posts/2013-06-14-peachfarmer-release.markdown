---
layout: post
title:  "Tool Release: PeachFarmer"
date:   2013-06-14 11:35:05
post_author: Michael Lynch
categories: tools
---

### Cloud-based Fuzzing with Peach

Several of the consultants here at iSEC perform fuzz testing using the [Peach fuzzing framework][peach-url]. One of Peach's strengths is that it allows the user to parallelize a fuzzing job between multiple machines, making Peach a great way to perform cloud-based fuzzing. The drawback of using Peach in the cloud is that each Peach instance generates a large number of log files and crash dumps. For the user to analyze their results effectively, they must aggregate all of these logs manually. With a large number of fuzzing instances, this can become a cumbersome task.


### PeachFarmer

To solve this problem, we created PeachFarmer. PeachFarmer runs as an agent on each Peach cloud instance. The user can query the fuzzing progress via the PeachFarmer client, which collects all of Peach's logs and crash dumps from each instance in the cloud. The client then downloads and aggregates these files to a central location on the user's local machine. PeachFarmer only downloads the data that has changed since the last successful check, so there's no redundant transfer of data files. In our own usage, PeachFarmer has made management of cloud fuzzing instances much faster and easier.


### Project Page

Today we are excited to release PeachFarmer to the security community. Check out the [project page on Github][peachfarmer-gh], try it out for yourself, and tell us what you think.

Happy fuzzing!


[peach-url]: http://www.peachfuzzer.com/
[peachfarmer-gh]: https://github.com/iSECPartners/PeachFarmer
