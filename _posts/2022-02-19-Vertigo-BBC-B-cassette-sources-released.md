---
title: "Vertigo BBC 'B' Cassette Version Released"
categories:
  - game sources
tags:
  - Vertigo
  - beebasm
  - ADE+
---

BBC 'B' cassette version sources are added to the BBC Master & BBC 'B' disc sources on the [GitHub repo](https://github.com/dr-grim/vertigo)!

![Vertigo BBC'B' cassette version, screenshot of Level 1 being loaded]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo cassette loading.png)

Much quicker again - boosted by the [`bash` script](https://github.com/dr-grim/vertigo/blob/main/original-dev-discs/convert_6502_src.sh) to speed up conversion from `ADE+` to `beebasm`.

This disc was slightly different to what I recalled - it has extra support to load the levels in from cassette, with messages such as "Rewind tape slightly" before starting the load.

Otherwise, the code looks suspiciously similar to the BBC'B'disc version, yet I remember the Electron version loaded all levels at the start. This may have been an interim version created during porting the BBC Master down to cassette. The disc was also partially incomplete - such as using `MODE 1` to load the `MODE 5` version of the title page! Fixed, so it loads properly - but I'm suspicious this version was never used.

Time to check the Electron version!