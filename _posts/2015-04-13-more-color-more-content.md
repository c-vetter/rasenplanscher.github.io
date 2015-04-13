---
title: More Color, More Content
---

I really did not like the clutter on the projects page, so I reduced that to just the titles. But that wouldn't do either... well, at least not terribly well -- that's why I also added project logos to the mix =) This day also saw the addition of another project, as well as several changes that were prompted by those new features.

So, the projects list. I think there really was too much going on there: two or three links per project, and you didn't even know what it's about? Not good. The tech lists were ok, I guess, from a conceptual standpoint; their presentation, however, was seriously botching up the cleanliness of this site. Lastly, I think a little eye-candy in the way of logos is nice. Having those logos in here, I thought, I'd add those to the project pages as well.

Getting the logos ready was just minor work:

* export SVG tiny from Illustrator
* clear out useless stuff, like xml prefix, doctype, groups, ids...
* trim whitespace
* save in convenient place

After that it was just scrapping the project list markup and adding `img` tags and styling the whole shebang. In parallel I already had an eye towards the latest project page ([about the brand UNSER](/projects/unser.html)) because I realized that my previous linking strategy wasn't going to fit that one semantically. The new project brought about two changes:

1. the `tech list` became the `skill list`
2. the several related URLs were folded into a single link list

For the second one, I went with [markdownify](http://jekyllrb.com/docs/templates/#filters) which produces `p` tags. That in turn led me to scrap the whole list thing around the links and just have several paragraphs of links -- works for me.

Back to the logos: I wanted to have them side by side and, in order to use the available optimally, to scale them depending on the viewport-width. Of course I wanted to avoid a whole lot of source code, so I wrote a few [mixins](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixins) to simplify the repetition. Those also came in handy in a few other places and I could reduce the existing code a little. So, it worked nicely all around =)

One issue though: I'm not comfortable yet with how my stylesheets look -- I'd like them to somehow be cleaner... Parameterizing everything occurred to me, and I'm gonna do that to some extent, but I don't think that's gonna cut it really =\ I will need to do some research on that...
