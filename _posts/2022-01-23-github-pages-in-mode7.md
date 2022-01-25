---
title: "GitHub pages in MODE 7"
categories:
  - blog
tags:
  - GitHub pages
  - MODE7 font
---

Proof of concept complete; time to blog!

Now, I needed a platform to host the trials and tribulations of extracting data from vintage discs. I looked around and had completely forgotten that [GitHub pages](https://pages.github.com) has support for blog hosting! I was looking to host any source code in GitHub, so that made it a no-brainer.

Next challenge - what template to use? There's a fair few out there, but I liked the look of [`minimal-mistakes`](https://mmistakes.github.io/minimal-mistakes/). Various styles, but nothing that quite said "BBC Micro". However, I tripped over [GALAX.XYZ](https://galax.xyz/TELETEXT) - a full copy of TeleText in a web page. I was in..

First mission was to get a local testbed so I could verify the pages before uploading - hopefully, avoiding publication errors. I used the [instructions](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll) from GitHub, showing how to install Jeykll.

I set up a Docker container to use `vscode` with it, to create a sandpit for me to work in. When first running Jeykll, it produced the following output:

```
vscode ➜ ~/retrograde (main) $ bundle exec jekyll serve
Your RubyGems version (2.7.6.2)) has a bug that prevents `required_ruby_version` from working for Bundler. Any scripts that use `gem install bundler` will break as soon as Bundler drops support for your Ruby version. Please upgrade RubyGems to avoid future breakage and silence this warning by running `gem update --system 3.2.3`
Configuration file: /home/vscode/retrograde/_config.yml
            Source: /home/vscode/retrograde
       Destination: /home/vscode/retrograde/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
      Remote Theme: Using theme mmistakes/minimal-mistakes
       Jekyll Feed: Generating feed for posts
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'assets/css/main.scss':
                    Invalid US-ASCII character "\xE2" on line 54
jekyll 3.9.0 | Error:  Invalid US-ASCII character "\xE2" on line 54
vscode ➜ ~/retrograde (main ✗) $
```

The error `Invalid US-ASCII character "\xE2"` was the error - I tracked it down c/o the internet, the fix needing `export LANG=en_US.UTF-8`; so, this time:

```
vscode ➜ ~/retrograde (main ✗) $ export LANG=en_US.UTF-8
vscode ➜ ~/retrograde (main ✗) $ bundle exec jekyll serve
Your RubyGems version (2.7.6.2)) has a bug that prevents `required_ruby_version` from working for Bundler. Any scripts that use `gem install bundler` will break as soon as Bundler drops support for your Ruby version. Please upgrade RubyGems to avoid future breakage and silence this warning by running `gem update --system 3.2.3`
Configuration file: /home/vscode/retrograde/_config.yml
            Source: /home/vscode/retrograde
       Destination: /home/vscode/retrograde/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
      Remote Theme: Using theme mmistakes/minimal-mistakes
       Jekyll Feed: Generating feed for posts
   GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.
                    done in 8.173 seconds.
 Auto-regeneration: enabled for '/home/vscode/retrograde'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```
The local copy was running nicely! I could now experiment.

The next challenge was to hook this in to `minimal-mistakes` eith minimal effort (no point re-inventing the wheel). Initially I took a full copy of the minimal-mistakes  repository to look where the fonts, style, etc were declared. I pulled the chanfes into a new theme: [`mode7`](https://github.com/dr-grim/retrograde/blob/main/_sass/minimal-mistakes/skins/_mode7.scss) which was placed in `_sass/minimal-mistakes/skins/_mode7.scss` to appear in the minimal-mistakes file path.

The underlying MODE7 font from [GALAX.XYZ](https://galax.xyz/TELETEXT) was placed in `assets/css/MODE7GX3.TTF`, referenced by the `mode7` style.

Time to push the changes to GitHub and see what we get :)