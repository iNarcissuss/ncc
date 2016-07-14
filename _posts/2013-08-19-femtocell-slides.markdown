---
layout: post
title:  "Black Hat 2013 - Femtocell Presentation Slides, Videos and App"
date:   2013-08-19 11:35:05
post_author: Tom Ritter
categories: conferences
download_name: Slides
download_link: https://www.isecpartners.com/media/106086/femtocell.pdf
github_name: FemtoCatcher
github_link: https://github.com/iSECPartners/femtocatcher
conference_name: Black Hat '13
conference_link: https://www.blackhat.com/us-13/briefings.html#Ritter
---


We're back from Las Vegas, rested, and finally ready to release the slides, videos, and our app from our presentation at Black Hat and Defcon: __Traffic Interception and Remote Mobile Phone Cloning with a Compromised CDMA Femtocell__.


### Slides and videos

The slides are available [here][slides-dl]. The videos of our demos are up on Youtube:

* [Phone Interception][phone-yt]
* [SMS Interception][sms-yt] 
* [MMS Interception][mms-yt]
* [Active Attack on Data Traffic][active-yt] 
* [Two-and-a-Half Way Phone Call][call-yt], demonstrating Cloning


### An Android app to detect femtocells

The CDMA Femtocells we examined differ from other types of personal wireless access points because the user does not have a choice in whether or not they connect to a femtocell.  Because your phone doesn't give you a choice when it comes to selecting what tower to connect to, the only way we could find to avoid communicating through a femtocell was to turn off the phone's cellular radio when it was connected to a femtocell.

Our __FemtoCatcher Android app__ is now available [on the Google Play Store][app-store], with source code available on [GitHub][app-gh].

FemtoCatcher runs on your Verizon Android smartphone and automatically switches your device into Airplane Mode, thus disabling all cellular connectivity, if it detects that your phone has connected to a femtocell.  While this does render your cellular connectivity unavailable in areas where the strongest signal is a femtocell, we would rather have no service than be connected to a tower that could be used by an attacker to intercept our communications. 

Some important notes on how FemtoCatcher works:

* FemtoCatcher uses the network ID information available through Android API calls to determine if the phone is connected to a Femtocell.
* We did not test how easy it would be for an attacker to change this information to fool the app, but certainly don't rule out the possibility.
* Some Verizon Android phones display an icon in the status bar and/or display an ERI banner of "Network Extender" when connected to a femtocell.  The strategy used by FemtoCatcher to detect the presence of a femtocell is based on the same techniques used by these indicators in Verizon ROMs.
* FemtoCatcher will not automatically take your phone out of airplane mode when you move away from a femtocell.  You will be without service until you manually re-enable your connectivity.  If FemtoCatcher is running and you are in range of a femtocell when you disable airplane mode, FemtoCatcher will quickly put your phone back in airplane mode.

Because of its imperfect and potentially confusing nature, we are not marketing FemtoCatcher to the general public, but rather to security minded people and those that are interested in femtocells.  We built this tool for our own testing, but we encourage you to poke at the source code and use it as you see fit.


[slides-dl]: https://www.isecpartners.com/media/106086/femtocell.pdf
[phone-yt]: http://www.youtube.com/watch?v=3FyNB4QmY1Q
[sms-yt]: http://www.youtube.com/watch?v=R-4fkJiVeE4
[mms-yt]: http://www.youtube.com/watch?v=uuwsMsvGAYo
[active-yt]: http://www.youtube.com/watch?v=2xjhtDobO8c
[call-yt]: http://www.youtube.com/watch?v=Ydo19YOzpzU
[app-store]: https://play.google.com/store/apps/details?id=com.isecpartners.femtocatcher
[app-gh]: https://github.com/iSECPartners/femtocatcher
