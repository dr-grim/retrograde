---
title: "Finally! DDOS2ADFS utility"
last_modified_at: 2022-02-01T18:15
categories:
  - data transfer
tags:
  - GoTEK
  - Opus DDOS
---

For those people struggling with a treasure trove of Opus DDOS format floppy discs. . .
![BBC Master 128k and discs]({{ site.url }}{{ site.baseurl }}/assets/images/vertigo-treasure-trove.jpeg)

After much fiddling, I've finally written a custom transfer program: [`DDOS2ADFS`](https://github.com/dr-grim/beeb-utils/blob/main/DDOS2ADFS/README.md). That's a link to a GitHub repo, `DDOS2ADFS` is stored in tokensied BASIC form and *SPOOL'd ASCII.

My problems with using `TreeCopy` (v1.61b), as far as Opus DDOS is supported, were:

1. When asking for "All subdirs", it seemed to act up - it might be scanning each DFS folder from A-Z etc., the drive was making interesting noises!
2. The disc sides weren't just 0 & 2, but 0A, 0B, .., 0H and 2A, .., 2H - which needed manual selection each time - and then a matching destination folder in ADFS.

So, the BASIC program I've written:
1. Scans the DDOS sectors on track 0 to discover what DDOS drive volumes are allocated
2. Scan each DDOS volume catalogue to read which files are present - and extract load & execution addresses, along with file length
3. Uses `OSWORD &7F` to read sector data
4. Uses `OSGBPB 1` and `OSGBPB 3` to read and write chunks of data
5. Plain `OSCLI` to `*SAVE` as a lazy way of setting load & execute addresses
6. `OSCLI` to `*CDIR` and `*DIR` in `ADFS` as required
7. Drive volumes in DDOS are mapped to subfolders in `ADFS`, so volume `0C` maps to folder `:0.$.0A` on ADFS
8. Files in folder `$` are copied to the root of the relevant volume folder
9. All other folders have a matching subfolder created in the relevant volume folder

Oddly, when using `*LOAD` in DDOS, then calling `*ADFS` to switch filing systems caused ADFS to lock solid - `ESCAPE` didn't work, had to use `BREAK`. This was circumvented by using `OPENIN` in BASIC and then `OSGBPB` to read the raw data - which has the advantage of being able to read a block of data from anywhere in the file.

`OSGBPB` enabled me to chunk large files - if the data wouldn't fit in memory, then it could be loaded and saved in multiple passes. `HIMEM` was set to be `LOMEM+&1800` - I have used way more memory than necessary due to long variable names. The code should be legible also neat'n'tidy with `LOCAL` variables - but that comes with a memory overhead. I'll take the hit for ease of maintenance.

However, given that this script was written just to copy Opus DDOS 720k floppy discs to ADFS 640k images on a GoTEK, I could make a fair few assumptions - and could use the folder layout I wanted. It didn't matter if it took many switches between file systems, as no physical media had to be swapped, and I could just leave it to run.

Hopefully there aren't any bugs - still being tested... but files seem to have landed safely :)

Any comments, I'll be on stardot.org & (allegedly) the GitHub [repo for the code](https://github.com/dr-grim/beeb-utils) will accept [issues](https://github.com/dr-grim/beeb-utils/issues).
