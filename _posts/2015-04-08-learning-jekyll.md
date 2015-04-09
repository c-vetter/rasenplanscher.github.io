---
title: Getting to know Jekyll
---

Today, I set out to create my first GitHub pages site. Looking at [the intro](https://pages.github.com/), that seemed simple enough. Therefore, I ventured to go the whole nine yards and do it in Jekyll right away. Here's what happened...


## Setting up ##

First, I setup my repository, installed Jekyll --using the `github-pages` gem-- and wrote my `_config.yml`, so as to partition my files in a manner that's more to my liking than the default. The default is not too bad, but I like to have a source directory and a destination directory on the same level, not one inside the other. Of course, later on, I learned that [GitHub pages does not support that](http://jekyllrb.com/docs/github-pages/) -- so, back to default-land :\

I want to use [compass](http://compass-style.org/) -- so, of course, I had to set that up as well. Compass is not included in Jekyll at this point, so I quickly [ducked for someone who has done that](https://duckduckgo.com/?q="github+pages"+compass), to save me some time there. I looked at [David Pots' post on that](http://davidpots.com/jekyll/tutorial/git/2013/06/24/jekyll-github-pages-compass.html#setting-up-compassscss). Unfortunately, for me that doesn't work because it relies on a custom plugin and GitHub Pages does not support those at this point. Otherwise I didn't see any promising posts, so, I'll have `compass watch` running while styling my site. Unfortunately, so far, that is kind of unreliable and just bails from time to time, so I'll have to look for another, more stable solution -- but that's for another day and another post. Also, I'll make sure to setup [git commit-hooks](https://git-scm.herokuapp.com/book/en/v2/Customizing-Git-Git-Hooks).

With the basic infrastructure in place, it was time to build my page scaffold. The first snag came pretty quickly, though: no markdown for includes by default O_o That struck me as rather counter-intuitive and I looked into it; I found [a workaround](http://wolfslittlestore.be/2013/10/rendering-markdown-in-jekyll/), which, of course, does not work either due to GitHub's safe mode. So, I was about to go ahead and use the filter workaround from the same post, despite its being less straight-forward... Taking a break that kept bothering me, and suddenly it dawned on me: I was just about to [abuse markdown](https://daringfireball.net/projects/markdown/syntax#html)! That's just not cool without a proper reason -- therefore, I'm glad I ran into this and realized I don't really want to go down that road. If the Jekyll developers built it that way for this purpose, I say "thank you for that"; if not, I'm still glad about it!


## Styling ##

Next up: making this baby beautiful :) I wanted to build a sleek interface that makes for nice reading on any device.

I started out with [normalize.css](https://necolas.github.io/normalize.css/) for the basics -- I believe it strikes a nice balance between cross-browser consistency and allowing for user-settings. That's rather important to me since I don't subscribe to the notion of "one size fits all" that a lot of designs bring with them in the form of pixel values.

### Typography ###

That meant, first of all, finding suitable fonts because any good visual design stands and falls with typography! I looked at all the fonts currently available through [Google Fonts](http://www.google.com/fonts) and found around a dozen that I liked and that would fit the bill. But to keep things simple, I whittled those down to three:

* [Maven Pro](http://www.google.com/fonts/specimen/Maven+Pro) for the headings
* [Noto Sans](http://www.google.com/fonts/specimen/Noto+Sans) for body copy
* [Anonymous Pro](http://www.google.com/fonts/specimen/Anonymous+Pro) for code samples

Those three work together nicely in creating a modern look without impairing legibility.

### Painting ###

With style consistency and fonts set, came the time to put some color on the chrome -- not too much though, because too much is bad for reading. Content is king, so I wanted to add precisely what is necessary to accentuate the content and not detract from it. I went with an almost achromatic theme, with just a smidgen of color for interactive elements. That same color is used in different tints throughout the site, but always so subtle that you can ignore it well enough to just read.

I also made a little favicon, just to have one for now. I'll go at it again later on, at which point I'll make a higher-quality version, and possibly an `apple-touch-icon` -- if I feel like it then.

The rest was just getting a few sizings in there so everything comes together like a chocolate cake :)


### IE fixing ###

Yeah, no biggy here: just hook up [the shiv](https://github.com/aFarkas/html5shiv/), put in a `<noscript>` stylesheet for those poor souls without JavaScript, and that's it. Having minimal styling and markup totally rocks in that regard =)

And yes, I am aware that it's highly unlikely that a lot of the two and a half percent of internet users that benefit from this will view this site in the foreseeable future -- but I'm just awesome like that. I wouldn't do a whole lot more than what I did, but that much is ok, I think.


## Conclusion ##

While the result so far is not perfect, I think it's good enough for the time being. I will be optimizing this whole thing in the future. Next up, however, I will add more content and some nifty gimmicks for people to ogle at :)


