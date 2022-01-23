---
title: "RetroClinic to the rescue!"
date: 2022-01-14
categories:
  - refurbish
tags:
  - PSU
  - RetroClinic
  - batteries
  - configuration
  - StarDot
---

![BBC Master PSU ready to send](/assets/images/BBC Master PSU ready to send.jpeg)

I'd extracted my PSU (as above!), and sent it in the post for Mark @ [RetroClinic](http://www.retroclinic.com) to look at. Also took an option on a [GOTEK](http://www.retroclinic.com/docs/GOTEKFloppyDrive.pdf) unit - so I could transfer from Opus DDOS into ADFS on a USB stick, which could then be read . . .

Mark replaced the burnt out caps, the mains lead and the switch - very neat job, plugged back in, and hey presto - a working BBC Master! Very pleased (and relieved nothing else had blown).

However, the configuration was lost as I'd removed the battery pack - "replace with Acorn parts" was written on the label, slight challenge there:

![BBC Master - battery unplugged](/assets/images/BBC Master battery case.jpeg)

However, mine was the "fix" Acorn applied which meant it was 3x AA batteries, a resistor and a diode - a replacement for a Lithium battery that could recharge explosively (!). My batteries were just 3 Duracell AA, so extracted, cleaned the contacts with vinegar (to dissolve the battery crud), scrubbed clean and ready to go with new batteries.

Now, to fix the configuration - there are various sources of info to remind the forgetful, but I found RetroClinic's [instructions](http://www.retroclinic.com/docs/MBAT_Guide.pdf) worked for me (although I'd not purchased the batteries from them). Also a good blog post from ["What Jessie Did Next"](http://blog.jessicat.me.uk/2009/10/cmos-reset-on-a-bbc-master-128/) - showing the use of random blogs - gives me faith! Also the [Official Acorn Application Note 203](http://stardot.org.uk/mirrors/www.bbcdocs.com/filebase/library/appnotes/AppNote-203.pdf) hosted by the amazing collection at [StarDot](http://stardot.org.uk). The magic technique is:

* Power on whilst pressing `R` until a message says `CMOS Reset`
* Then press `CTRL`-`Break`
* Then `CTRL`-`F`-`Break` to enter "Supervisor" mode - and start configuring
* `*CONFIGURE FILE 3` (my disc system is Opus DDOS - in a cartridge slot)
* `*CONFIGURE LANG 12` (so BBC BASIC starts up)
* `*CONFIGURE MODE 7` (initial screen mode - TeleText!)

Right then, onto the discs!