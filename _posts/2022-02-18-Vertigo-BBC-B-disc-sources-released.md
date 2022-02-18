---
title: "Vertigo BBC 'B' Disc Version Released!"
categories:
  - game sources
tags:
  - Vertigo
  - beebasm
  - ADE+
---

BBC 'B' disc version sources are added to the BBC Master sources on the [GitHub repo](https://github.com/dr-grim/vertigo)!

![Vertigo BBC'B' disc version, screenshot of Level 1, Screen 5]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo-BBC-B-disc-version-lvl1scn5.png)

Onwards and upwards - making a [`bash` script](https://github.com/dr-grim/vertigo/blob/main/original-dev-discs/convert_6502_src.sh) to speed up conversion from `ADE+` to `beebasm` has paid dividends.

I've extended the `bash` script to further reduce the manual fixes, at the cost of it hiding things that need to be modified, but it saves me time as I'm back in the pattern of the code.

Next challenge: the BBC 'B' cassette version. Being a pedant, this will generate a disc image that can make a cassette . . . I've not used `beebasm`'s cassette functionality, so it'll be interesting to test :o)