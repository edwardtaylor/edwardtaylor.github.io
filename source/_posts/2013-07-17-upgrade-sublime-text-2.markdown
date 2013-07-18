---
layout: post
title: "Upgrade Sublime Text 2"
date: 2013-07-17 21:08
comments: true
categories: [linux, how-to]
---

I've been developing primarily on Windows-based machines and slowly learning (and loving) developing on Linux. My distro of choice is the popular Ubuntu environment mainly due to the overwhelming number of people that also use this distro to develop Rails applications.

[Sublime Text](http://www.sublimetext.com) is an fantastic text editor and becoming my go-to editor of choice for code. The last time I've preferred 
a text editor over a full-blown IDE was back in my college days when SSHing
into a DEV environment in using vi was the only way I could quickly submit 
a class project minutes for the midnight deadline.

After walking through the steps to install Sublime Text it was now time for an upgrade, a new experience for me. Listed below are the steps I took to remove my previous installation and use the new deb installation provided by SublimeText.

###Step One - Remove the old files

Remove the previous installation located at `/usr/lib/sublime-text`

**Note:** The installation directory may vary so use [find](http://unixhelp.ed.ac.uk/CGI/man-cgi?find) to locate and remove and files from the previous version.

###Step Two - Remove application links

Remove any application links at `/usr/share/applications/`

Read more about the [Linux Directory Hierarchy](http://www.tldp.org/HOWTO/HighQuality-Apps-HOWTO/fhs.html)

###Installing Sublime Text 3 (debian package)

1. Go to the [download page](http://www.sublimetext.com/3) and download the **deb** package installer for your processor. 

2. Open the package installer using **Ubuntu Software Center** and install

3. Navigate to `/usr/share/applications/` and drag the sublime-text.desktop icon over to your Unity launcher for quick access

4. (Optional) If you would like to position the icon in your list, click and hold (1 second), then icon will lift from the Unity bar and allow you to reposition.

References:

* http://www.sublimetext.com/
* https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles
* http://www.tldp.org/HOWTO/HighQuality-Apps-HOWTO/fhs.html
* http://en.wikipedia.org/wiki/Deb_(file_format)



