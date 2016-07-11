---
layout: post
title:  "Blackbox Android App Analysis with Introspy"
date:   2013-12-13 13:42:42
post_author: Marc Blanchou & Alban Diquet
categories: android introspy conferences
---


As previously announced during our [Ruxcon presentation][ruxcon-post], we're
now releasing [Introspy for Android][gh-page]. The final version of the tool
was demonstrated at the [iSEC Open Forum][openforum] here in San Francisco.

### Blackbox Android Pentesting

Similarly to the [iOS version][introspy-ios] that was released a few months
ago, Introspy for Android is a tool designed to help penetration testers
understand what an Android application does at runtime, and to greatly
facilitate the process of reviewing the application's security mechanisms.

The tool can easily be installed on a rooted device running [Cydia
Substrate][cydia] and provides a GUI interface to configure hooks, filters and
options. See the [project page][project-page] as well the
[slides][introspy-slides] we presented at the Open Forum for more information
about what the tool does and how it works.

Source code and pre-compiled packages are available on the project's [source
repository][project-page] on Github.


[introspy-ios]: https://github.com/iSECPartners/Introspy-iOS
[openforum]: http://www.meetup.com/iSECOpenForums/
[project-page]: https://github.com/iSECPartners/Introspy-Android
[gh-page]: https://isecpartners.github.io/Introspy-Android/
[ruxcon-post]: ios/android/introspy/ruxcon/2013/10/27/introspy-slides-ruxcon-2013.html
[introspy-slides]: /publications/2013.12.13-isec-openforum-introspy.pdf
[cydia]: http://www.cydiasubstrate.com/
