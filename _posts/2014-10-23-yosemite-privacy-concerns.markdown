---
author: ian_mcxa
comments: true
date: 2014-10-23 03:06:38+00:00
layout: post
slug: yosemite-privacy-concerns
title: Yosemite Privacy Concerns
wordpress_id: 833
categories:
- General
- OS X
post_format:
- Gallery
tags:
- osx
- privacy
- security
- Yosemite
---

There are currently a few sites out there detailing some privacy concerns with 10.10 Yosemite, and recommending a few fixes. However, there is a bit more going on that what's getting the most attention.


### Spotlight


To help improve searching, Apple records your spotlight searches. This is a little sketchy, but I can see why they would do it. It makes spotlight more helpful. This can be disabled under System Preferences > Spotlight > Search Results.

Safari also has a spotlight suggestions option which sends your searches to Apple. Keep in mind that this will happen even if you are using a secure search engine such as [Duckduckgo](ddg.gg) or [Startpage](https://www.startpage.com/). This can also be disabled in Safari's preferences; however, I would still recommend against using Safari as your primary browser.


### Mail


If you set up an account through the mail app, the domain will be  sent to Apple for some reason. This means nothing if you use gmail or similar large scale services, but it could be unnerving to users of accounts on smaller domains. The solution to this is to simply use web based mail applications or something like Thunderbird.


### About this mac and Cookies


Now for the interesting stuff. Whenever you open about this mac, data is transmitted to Apple including a cookie that is used to uniquely identify users. This cookie tracks the IP address that you initially visited Apple.com from, as well as the IP addresses from all subsequent connections to Apple through Spotlight or Safari. There appears to be no way to disable this. The data is still sent to Apple even if you have location tracking turned off, and have not signed into iCloud.


### Conclusions


If you' are concerned about your privacy, it might not be best to upgrade to Yosemite yet. The fix-macosx people are looking at solutions with firewalls to limit this data collection. Moreover f you really have something to hide, you probably shouldn't digitize it at all, and if you must I recommend using a secure OS such as [Tails](https://tails.boum.org/).


### Sources


https://github.com/fix-macosx/yosemite-phone-home

https://fix-macosx.com/
