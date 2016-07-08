---
layout: post
title:  "iOS Secure State Preservation"
date:   2013-09-18 11:35:05
post_author: Tom Daniels
categories: ios, crypto
---

iOS 6 introduced the concept of application state preservation. The purpose of
state preservation is to hide unexpected application termination from users.
Regardless of why the application was terminated (e.g., the user explicitly
kills the app or the system terminates it to free up memory for the foreground
application), state preservation allows users to return directly to the last
point of use within the app to provide as smooth a user experience as possible.
This is achieved by serializing the state of your app's view controllers and
views when it is backgrounded and storing them to disk.

For a detailed explanation of the preservation and restoration process, refer
to Apple's State Preservation and Restoration [Programming
Guide][state-guide].

### SecureNSCoder

Developers need to be careful when persisting view states, as there is the
potential to expose sensitive application information since the serialized data
is in plaintext. Therefore, any data that should remain private needs to be
appropriately protected from offline recovery. As such, iSEC created a [sample
application][securecoder-gh] that implements a more secure process for state
preservation and restoration by encrypting objects before encoding and writing
them to disk. The goal was to provide developers with a reference for securely
implementing state preservation so they can protect their application data while
still providing users with an uninterrupted experience.

The NSCoder subclasses for key-based encoding, NSKeyedArchiver and
NSKeyedUnarchiver, define delegate protocols that allow applications to
customize the encoding and decoding processes, including manipulation of the
objects to be (de)serialized. By using a custom class that implements these
delegate protocols we can serialize objects, encrypt them with a key from the
Keychain, and then pass them back off to UIKit for preservation. When the app is
relaunched the data is decrypted and deserialized before being reinstantiated by
the view controller. Through implementing the delegate protocol, developers can
take fine grained control over which objects are encrypted or simply encrypt all
state information.

### Project Page

Check out [the project page on GitHub][securecoder-gh] and try out secure state
preservation in your apps!

[state-guide]: https://developer.apple.com/library/ios/documentation/iphone/conceptual/iphoneosprogrammingguide/StatePreservation/StatePreservation.html
[securecoder-gh]: https://github.com/iSECPartners/SecureNSCoder
