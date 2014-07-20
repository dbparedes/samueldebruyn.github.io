---
author: Sam
comments: true
date: 2014-02-08 09:47:34+00:00
layout: post
slug: secure-ssh-access-with-2-step-authentication-extended
title: Secure SSH access with 2-step authentication (extended)
wordpress_id: 92
categories:
- English
- Linux
---

In this quick tutorial I'll show you how to secure SSH access to your Linux server with 2-step authentication. Why did I call this post 'extended'? Because I'll show you how to add extra rules so you don't have to use 2-step authentication from certain locations.<!-- more -->

I'm not going to explain [what 2-step authentication is](https://support.google.com/accounts/answer/180744). You'll need SSH or CLI access to your Linux device with root rights and a 2-step authentication app on your phone, tablet or PC:



	
  * [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2)

	
  * [iOS](https://itunes.apple.com/nl/app/google-authenticator/id388497605)

	
  * [Windows Phone](http://www.windowsphone.com/en-us/store/app/authenticator/021dd79f-0598-e011-986b-78e7d1fa76f8)

	
  * [BlackBerry](http://m.google.com/authenticator)

	
  * [more....](http://www.howtogeek.com/129014/how-to-use-google-authenticator-and-other-two-factor-authentication-apps-without-a-smartphone/)


The PAM-module that we need is called _libpam-google-authenticator_ so on Debian/Ubuntu/... you can use the following command to install this:

[code]sudo apt-get update && sudo apt-get install -y libpam-google-authenticator [/code]

Next, run

[code]google-authenticator[/code]

to set this up for your account. Do not use _sudo_ or something like that, use your own account!

Now open the file _/etc/pam.d/sshd,_ you[ can do this](https://help.ubuntu.com/community/Nano) with

[code]sudo nano /etc/pam.d/sshd[/code]

and add the following at the end of the file:

[code]

auth [success=1 default=ignore] pam_access.so accessfile=/etc/security/access-local.conf
auth required pam_google_authenticator.so

[/code]

Now create the file_ /etc/security/access-local.conf_:

[code]sudo nano /etc/security/access-local.conf[/code]

and add the following:

[code]

+ : ALL : ????
+ : ALL : LOCAL
- : ALL : ALL

[/code]

Replace the ???? with the subnet or the IP that should be allowed to access SSH without the second verification step. [You could enter](http://linux.die.net/man/5/access.conf) an IP like _192.168.0.5_ or a subnet like _192.168.0.0/24_.

Now edit the file _/etc/ssh/sshd_config_:

[code]sudo nano /etc/ssh/sshd_config[/code]

and make sure it says

[code]ChallengeResponseAuthentication yes[/code]

By default it says _no_.

Now restart the SSH service and you should be good!

[code]sudo service ssh restart[/code]


## NTP


Ahtanu has [let me know](https://twitter.com/ahtanu/status/432092745348677632) via Twitter that you'd better make sure your device is properly configured as an NTP client. Most desktop Linux distributions have this already in order but here are the instructions for Debian-based distributions to make sure NTP is configured properly.

First, update or install the NTP client.

[code]sudo apt-get update && sudo apt-get install -y ntp ntp-simple ntpdate[/code]

Next, set the timezone and the date on your device:

[code]
sudo tzselect
sudo date --set 2014-12-31
sudo date --set 20:20:20
[/code]

Now edit the file ntp.conf:

[code]sudo nano /etc/ntp.conf[/code]

and make sure it has 2 NTP-servers:

[code]
server 0.be.pool.ntp.org
server 1.be.pool.ntp.org
server 2.be.pool.ntp.org
server 3.be.pool.ntp.org
[/code]

Eventually restart the NTP service:

[code]sudo service ntpd restart[/code]
