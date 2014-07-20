---
author: Sam
comments: true
date: 2013-12-09 22:44:12+00:00
layout: post
slug: connecting-serviio-with-telenets-yelo-tv
title: Connecting Serviio with Telenet's Yelo TV
wordpress_id: 22
categories:
- home media
---

# Introduction


Recently Belgian ISP Telenet [introduced](http://snap.telenet.be/nieuw/artikel/yelo-tv-getest-en-gekeurd) [Yelo TV](http://telenet.be/nl/yelo-tv). It's the new brand for all of their efforts <del>to </del><del>innovate</del> with television. Yelo TV includes a series of apps for almost every device (except for Windows Phone) and a [website ](http://yelotv.be/)on which you can watch live television, watch recordings or schedule recordings. 

<!-- more -->

During the coming weeks Telenet is also updating their [DigiCorders](http://telenet.be/nl/digitale-tv) to a new software version called Yelo TV. Most of the changes are in design but the new firmware will include a [DLNA](http://en.wikipedia.org/wiki/Digital_Living_Network_Alliance) renderer. This means that you can use any device with a DLNA server to stream music, photos and videos to a television connected to a Telenet DigiCorder.

I have a computer with [Serviio](http://www.serviio.org/) on it. Serviio is a free DLNA server (a Pro version with more features is available) and in my opinion it's the best available. Serviio includes support for transcoding. This way Serviio will convert every media file in a format which the DLNA renderer is able to play if necessary.

DLNA has its advantages and disadvantages, one of the latter is difficulties to detect compatible media formats. That's why Serviio uses _profiles_ which define the compatible media formats for each type of DLNA renderer.

There wasn't one for Telenet Yelo TV yet so I wrote one. This profile will convert every incompatible media file so that you can stream it to your DigiCorder. You'll need a fast computer to transcode files. This profile includes support for subtitles if you enabled it in Serviio's Console.


# Update: Plex


I recently switched to Plex. A profile for Plex is available [on my GitHub](https://github.com/SamuelDebruyn/yelotv-plex-profile/blob/master/yelotv.xml) (forked).


# The profile:


[gist id=7944739]


# Installation


This profile will soon enough be included in a future update of Serviio. If you'd like to use this profile before version 1.4 is released, follow these steps:



	
  1. I've included [a complete profiles.xml file (packaged as a profiles.zip file)](http://blog.sa.muel.be/?attachment_id=48) for Serviio 1.3.1. Download and unpack this file.

	
  2. Right click the Serviio Console icon and click on "Leave Serviio"

	
  3. Paste and overwrite the profiles.xml from above in the _config_ directory in Serviio's installation directory (probably _C:\Program Files\Serviio\config_).

	
  4. Restart your computer.


Enjoy!


# NB: Further optimizations


Tips to get a **higher video quality** (only works for videos that have to be transcoded because of incompatibility or that include subtitles):



	
  * Before you paste this profile in the profiles.xml file, find and replace _mpeg2video_ with _h264_


Tips to get a **lower video quality** (solves problems when the video stutters):



	
  * Improve your network connection (Telenet offers a [Funcheck](http://telenet.be/nl/funcheck) if you can't do this yourself)

	
  * Before you paste this profile in the profiles.xml file, find and replace _targetVCodec="mpeg2video"_ with _targetVCodec="mpeg2video" maxVBitrate="4096"_

	
  * Encode all your videos to H264/AAC in a mp4-container

	
  * For technical users only: you could force Serviio to always transcode videos, look at [_forceVTranscoding_ ](http://www.serviio.org/index.php?option=com_content&view=article&id=24)and [_alwaysEnableTranscoding_](http://www.serviio.org/index.php?option=com_content&view=article&id=16)


