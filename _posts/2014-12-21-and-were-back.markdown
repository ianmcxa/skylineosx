---
author: ian_mcxa
comments: true
date: 2014-12-21 06:51:38+00:00
layout: post
slug: and-were-back
title: And We're Back
wordpress_id: 865
categories:
- General
---

### Hacked


If you've tried to browse to this site in the past few days, you might have noticed a large red warning page saying the site contains malware.  We were hit by the SoakSoak wordpress attack. It attacks a site through the Revolution Slider plugin, and proceeds to install backdoors and malware into a site. This malware attempts to covertly download code from the domain soaksoak.ru.


### Protecting Yourself


Considering the events of the past few days, I thought it might be nice to do a little bit on security.

For us hackintoshers, there isn't as much of a chance for hacking and viruses as on windows. The basics still apply though. Update your machine as soon as there are updates available, don't install questionable software, and use a secure browser such as Firefox, Chrome or Safari.  That will just about do it for a normal users; however, if you need to go a step beyond I have a few suggestions.


#### [No Script](https://noscript.net/)


The largest opening modern desktop computers have to the outside world is through browsers, or more specifically through Javascript. Javascript exposes a lot of information and has been behind numerous attacks in the past. It is not fundamentally insecure, but the nature of it's functionality means that exploits are common. Noscript is a browser plugin that allows you to restrict javascript to only run from domains that you trust. If you block all javascript the web becomes fairly unusable, so only use this if you're alright with going through and allowing scripts from sites you trust.


#### [KyPass](http://www.kyuran.be/logiciels/kypass4mac/)


KyPass is an OSX port of KeePass, a popular password safe for windows. KyPass is unlocked with a master password, and stores all your passwords. This way you can easily use different passwords for every login. This means that if one site is compromised and your password is stolen, your other logins are safe. KeePass is also available on virtually every platform.


#### Encrypt Your Hard Drive


Most people aren't aware that if your hard drive isn't encrypted, I can simply take your computer, boot it off a USB drive and access all your data. Setting a BIOS password won't stop me either; I can just pull the BIOS battery and everything is reset. If you have any data that you wouldn't be comfortable with the world seeing on your hard drive, especially if it is a laptop I recommend encrypting your hard drive.  You can do this in disk utility, by adding an encrypted volume, and placing your files inside.

Anyway, our site is fully functional again. Happy Holidays, and stay safe out there.


### Sources


https://wordpress.org/support/topic/soaksoakru-malware

http://thehackernews.com/2014/12/SoakSoak-Wordpress-Malware.html

http://blog.sucuri.net/2014/12/revslider-vulnerability-leads-to-massive-wordpress-soaksoak-compromise.html
