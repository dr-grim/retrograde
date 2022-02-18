---
title: "Vertigo Sources Released!"
categories:
  - game sources
tags:
  - Vertigo
  - beebasm
  - ADE+
---

I've extracted and ported the code from the Vertigo Master backup disc - now build via `beebasm` and binary matches the discs!
![Vertigo title screen]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo-titlescreen.png)

# ADE+ to beebasm
Nothing's ever simple. . . mostly a mapping of assembler directives to get it to work (ref. [`beebasm` source syntax](https://github.com/stardot/beebasm#5-source-file-syntax) and [`ADE+` source syntax](http://archive.retro-kit.co.uk/bbcdocs.com/filebase/adsplus.pdf)), namely:

`ADE+` | `beebasm`
-|-
`label <instructions>` | `.label <instructions>`
`* commment` | `; * comment`
`EQU` | `=`
`DB` or `DFB` | `EQUB`
`DW` | `EQUW`
`DS` | `SKIP`
`ENDM` | `ENDMACRO`
`ASC <str>` | `EQUS <str>`
`STR <str>` | `EQUS <str>, &0D`
`TTL` | commented out
`LST` | commented out
`CHN` | `INCLUDE`
`#<-ve number>` | `#<-ve number> AND &FF`

The last issue was where negative numbers were not supported with (e.g.) `LDA #-8` - work-around was to `AND &FF` to get the 8 least-significant bits
which gave the 2's complement value I needed. Also I needed to convert line endings from `\r` to `\n`; all fairly strightforward, except this:

`ADE+` | `beebasm`
-|-
`<` | `>` or `LO`
`>` | `<` or `HI`

Now that one DID catch me out! Why they used different orientations I'll never know, but once you know. . . the collection of mappings were implemented as a [shell script](https://github.com/dr-grim/vertigo/blob/main/original-dev-discs/convert_6502_src.sh) to ensure repeatability - and make life easier given the number of files and discs to convert.

# From code assembling to disc assembling

Slight change, of course - a stand-alone 6502 executable isn't much use without the rest of the disc contents, and emulators much prefer disc images. Luckily, `beebasm` outputs a disc image directly - I just needed
to add in directives for the other data and assembly files.

The bitmaps and binary data files were just added to the `src` folder, then using the `PUTFILE`
directive - after making a careful note of the `.INF` file contents (load and execution addresses). To neaten the code, I moved all the "INCLUDE" directives to the `main.6502` file - this has macros, zero page workspace allocation and the directives for file loading. This means the "setup" is all in one file, including adding the binary files to the disc image.

The `bank4` and `bank5` files are various bits loaded into the 16kB RAM banks on the BBC Master 128k - these are bitmaps and the game levels. Side `2` of the disc constructs this.

# What's next?
Not everything has been pulled over, the level editor, sprite tools, etc. have yet to be transferred. The `bank4`and `bank5` files are currently just binary images too, rather than built. I'll hold off on those until the main assembly code is ported over for the other versions (BBC 'B' disc, BBC 'B cassette, Electron cassette). I can then make head or tail of the code tweaks between the versions and merge into a single common source repository - rather than four mostly similar but not quite source folders . . . to be continued!