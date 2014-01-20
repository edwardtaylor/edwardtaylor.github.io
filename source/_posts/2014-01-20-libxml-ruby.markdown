---
layout: post
title: "libxml-ruby"
date: 2014-01-20 11:57
comments: true
categories: [rails, osx, errors]
---

**Problem:** libxml-ruby (2.3.3) is not compatiable with libxml versions 2.9.X

**Environment:** OS X Version 10.9.1 (Mavericks)

**Error Message:** 

```
ruby_xml_node.c: In function ‘rxml_node_to_s’:`
ruby_xml_node.c:622: error: dereferencing pointer to incomplete type`
ruby_xml_node.c:624: error: dereferencing pointer to incomplete type`
```

**Resolution:** 

```
export SDKROOT=/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk
```

XCode command line tools on Mavericks includes version 2.9.0 `#define LIBXML_DOTTED_VERSION "2.9.0"` in 
`/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.9.sdk/usr/include/libxml2/libxml/xmlversion.h`

The 10.8 SDK uses version 2.7.8 which is compatiable with the older libxml-ruby 2.3.3 version. Support for libxml version 2.9.x wasn't added until version 2.4.0 of libxml-ruby. [HISTORY](https://github.com/xml4r/libxml-ruby/blob/master/HISTORY)

If we run the following command, we can see which SDK version is being included
```
$ xml2-config --cflags

-I/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.9.sdk/usr/include/libxml2
```

Opening up the xml2-config script, I noticed it's using [xcrun](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/xcrun.1.html) to return the CFLAGS used when building libxml. After reading the documentation, we can target a different version of the SDK by using the SDKROOT environment variable.

	SDKROOT

	Specifies the default SDK to be used when looking up tools (some tools may have SDK specific  versions).

	This  environment  variable  is also set by xcrun to be the absolute path to the user provided SDK (either via SDKROOT or the --sdk option), when it is used to invoke a normal developer tool (build tools like xcodebuild or make are exempt from this behavior).


After targeting the correct SDK and pulling libxml version 2.7.8, the gem successfully installs.


###Resources:

* [Project Page - LibXml-Ruby ](http://xml4r.github.io/libxml-ruby/)
* [xcrun(1) Mac OS X Developer Tools Manual Page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/xcrun.1.html)
* [LibXml FAQ: xml2-config](http://www.xmlsoft.org/FAQ.html)


