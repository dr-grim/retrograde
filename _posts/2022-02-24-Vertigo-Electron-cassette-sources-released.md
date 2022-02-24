---
title: "Vertigo Electron Cassette Version Released"
categories:
  - game sources
tags:
  - Vertigo
  - beebasm
  - ADE+
---

Electron cassette version sources are added to the BBC Master & BBC 'B' disc sources on the [GitHub repo](https://github.com/dr-grim/vertigo)!

Fast turnaround again - boosted by the [`bash` script](https://github.com/dr-grim/vertigo/blob/main/original-dev-discs/convert_6502_src.sh) to speed up conversion from `ADE+` to `beebasm`.

The Electron variant is a single cassette load, whereas the BBC 'B' cassette version was a multi-load. The Electron hasn't got the music (as it only has one sound channel vs three with the BBC - noting both had an additional noise channel); the Electron version just has the sound effects. To avoid missing the music, instead of in the game, it is included in the file loader (played when the title screen is displayed - only one channel sound, but it won't clash with the sound effects). 

The animation Easter egg is also removed - this meant that there was just enough space to store the game with all the levels and the end-of-level animations. We did, however, have make use of various chunks of unused memory to enable the code to fit (such as the printer buffer).

An additional challenge was that the Electron ran at 1MHz in RAM, compared to 2MHz for the BBC 'B' / Master; so it ran at half speed with user code. To make the game feel as if it ran at the same speed on both platforms, the Electron runs two passes through the movement code before rendering. The "go-behind" routine (where the ball is hidden by the blocks) was slow to run - it was complex! So, skipping this and running the physics twice, we got twice the movement in half the time. This results in the slower Electron playing at the same speed as the BBC version.

With this source code conversion, the `INCBIN` directive in `beebasm` really helps - the sources now directly include the binary data, rather than as previously with `ADE+` the data was merged in as a post-process.

All versions are now uploaded, and I've also stored the `SSD`/`UEF` files in the root of the [GitHub repository](https://github.com/dr-grim/vertigo):
* [BBC Master discM (SSD format)](https://github.com/dr-grim/vertigo/blob/main/vertigo.ssd?raw=true)
* [BBC 'B' disc (SSD format)](https://github.com/dr-grim/vertigo/blob/main/vertigo-bbc-b-disc.ssd?raw=true)
* [BBC 'B' cassette (UEF format)](https://github.com/dr-grim/vertigo/blob/main/vertigo-bbc-b-cassette.uef?raw=true)
* [Electron cassette (UEF format)](https://github.com/dr-grim/vertigo/blob/main/vertigo-electron-cassette.uef?raw=true)

Next challenge - tidying up the common code and data! The four build variants should really share a common code and data base; it only ended up this way as I wasn't needing to back-port any changes from version to version, it was a one-way trip of version creation.