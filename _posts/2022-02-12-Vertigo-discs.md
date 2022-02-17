---
title: "Vertigo disc retrieval"
categories:
  - data transfer
tags:
  - Vertigo
  - floppy cleaning
---

Now had the time to clean the discs (with Isopropyl alcohol) and remove mould/dust/grot; I've fed them through [`DDOS2ADFS`](https://github.com/dr-grim/beeb-utils/blob/main/DDOS2ADFS/README.md) (and fixed a few bugs :) ).

# Disc fault
Just a note to say that discs that "look" clean still can't be trusted, sometimes you've really got to get your eye in to spot dirt. You have to catch the light to see the matt vs shiny area to see mould. In the meantime, here's a few more obvious ones:

![white debris on disc surface]({{ site.url }}{{ site.baseurl }}/assets/images/Disc-case-degraded.jpeg) | ![subtle dirt on disc surface]({{ site.url }}{{ site.baseurl }}/assets/images/Disc-subtle-dirt.jpeg) | ![mould spot on disc surface]({{ site.url }}{{ site.baseurl }}/assets/images/Disc-mould-spot.jpeg)
-|-|-
Breakdown of casing? | Subtle dirt  | Perfect example of a mould spot

Note sheen on disc case - needed reflection to highlight dirt.

# Vertigo retrieval
Anyway, here's the synopsis of the data retrieval so far, in rough order of age...:

Photo | Note on disc contents
-|-
![RAB New Master Disc BBC MASTER 128k *1991* - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/RAB New Master Disc BBC MASTER 128k *1991* - thumbnail.jpeg) | Roll-A-Ball New Master Disc (for BBC Master 128k); before we'd polished the game with advice from Superior Software.
-|-
![Roll-A-Ball Master backup - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Roll-A-Ball-Master-backup - thumbnail.jpeg) | Roll-A-Ball Master backup - I usually kept two physical copies just in case. Floppy discs were a precious commodity when in school - spot the recycling!
-|-
![Sound and music development disc - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Sound and music development disc (faulty) - thumbnail.jpeg) | Sound and music development disc - urgh, couldn't get this one to work. This had the white detritus as shown above - I think the sleeve has degraded.
-|-
![Vertigo - Game music - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo - Game music - thumbnail.jpeg) | Vertigo - Game music, this was a late addition (we got the game working before making it a better package).
-|-
![Vertigo Master backup - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo-Master-backup - thumbnail.jpeg) | Vertigo Master backup - probably the root copy that the later versions come from.
-|-
![Vertigo BBC'B' *1991* (DISC) FAULTY - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo BBC'B' *1991* (DISC) FAULTY - thumbnail.jpeg) | Vertigo BBC'B' disc version - alas, another faulty disc I can't retrieve.
-|-
![BBC'B' CASSETTE VERSION VERTIGO - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/BBC'B' CASSETTE VERSION VERTIGO - thumbnail.jpeg) | BBC'B' cassette version - can't recall difference between the disc & cassette versions for the BBC 'B' - possibly the disc one loads the levels in on demand.
-|-
![Vertigo disc protection - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo disc protection - thumbnail.jpeg) | Vertigo disc protection - stops simple piracy, also 40 track reader for 80 track drive.
-|-
![Vertigo loading code - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo loading code - thumbnail.jpeg) | Vertigo loading code - eye candy!
-|-
![Vertigo tape compactor - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo tape compactor - thumbnail.jpeg) | Vertigo tape compactor - forgotten we had this, must have tried to make it less painful for cassette users.
-|-
![Vertigo tape loader - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo tape loader - thumbnail.jpeg) | Vertigo tape loader - using the compacted files.
-|-
![Vertigo+Pipemania compressed loader - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo+Pipemania compressed loader - thumbnail.jpeg) | Vertigo+Pipemania compressed loader - so the two games would fit on a single 100kb 40T disc.
-|-
![Vertigo - electron - thumbnail]({{ site.url }}{{ site.baseurl }}/assets/images/Vertigo - electron - thumbnail.jpeg) | Vertigo - electron - tweaked version of BBC'B' variant.

# Synopsis

Well, not bad to be honest - I think I've got what I need to get the sources back for all versions. Due to the lack of version control, there's a lot of duplication - the BBC'B' disc will contain mostly the same contents as the BBC'B' cassette version, rather than conditional assembly.

Only real "casualty" is the "Sound and music development" disc - seems that white floppy discs don't stand the test of time. That had various experiments with music & sfx on it. Ironically, other cheap, unbranded discs are fine - and have survived better than the Scotch 3M discs.

Next mission: start sifting and uploading to GitHub! I'll start with the Master 128k disc, upload that and get it working with `beebasm` so it can be rebuilt off-beeb. Then onto the other discs - and finally to "diff" what I tweaked. . .