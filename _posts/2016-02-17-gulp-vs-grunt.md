---
title: Which fruit is better – gulp or Grunt?
---

When people ask which one is better, [Grunt](http://gruntjs.com/) or [gulp](http://gulpjs.com/), what ensues is usually a comparison of apples and oranges. Both are task runners/fruit, and they can do the same things. Their flavors are different, however, and the oversight of not treating both as what they are, seems to be getting in the way for some people. Therefore, here's my take on the matter.

## tl;dr
Both tools do their work and have thriving eco-systems full of good ideas and tools; and by cross-pollination you won't have great feature-disparities most of the time. Grunt is somewhat simpler (without being any less powerful!), gulp somewhat more flexible. It all comes down to personal taste, as long as you use both tools the way they are meant to be used.

## Comparison as fruit
Both Grunt and gulp are task runners, basically. By loading third-party modules, they get the ability to do just about everything that fits in that scope. Just as both apples and oranges will give you fructose, vitamins, and water, both tools will give you everything you need to automate your most common tasks – which is why they're happily used as build tools, and they both fill that role well.

Although gulp is somewhat younger, you'll find plugins for juat about everything you need for it, just like Grunt. And since the target audience for Grunt is pretty much identical with gulp's, both communities continually include new modules from the other into their own environments, and that is not going to change anytime soon.

## The Flavor makes the Choice
Where they differ is in the details. That does not mean, the differences are trivial, however. Both tools approach their role differently.

### Grunt: The Sweet Taste of the all-mighty Apple
Grunt's way of doing things is basically:

* Read configuration (Gruntfile.js)
* Resolve requested task into sub-tasks
* For each sub-task:
  * Read input-files
  * Pipe into modules referenced in task configuration
  * Write output files

### gulp: Enter the exotic one: the orange
gulp's way of doing things boils down to this:

* Execute bootstrap code (gulpfile.js), including task definitions
* Execute requested task
* Inside each task you'll typically do:
  * Create stream from input files
  * Pipe into modules called in task code
  * Write output files from stream

### How's it taste?
On the face of it, both tools look pretty similar, and in many regards they are. Once you use both, you will immediately become aware, that they taste quite differently. Grunt is very much configuration-based, gulp code-based. Grunt is file-based, gulp is stream-based.

#### Simplicity versus Flexibility
Although a Gruntfile is technically a script file, in practice you do very little that you couldn't do in a JSON file just as well. That makes Grunt very simple to use. gulp uses actual, proper code to define tasks. That means, you can do all the shenanigans you want out of the box, where you'd have to work hard to get it just the way you want in Grunt. Also, gulp tends to lean a little more on the side of small files than Grunt does.

In my view, both tools' advantages at this point more or less cancel each other out effectively and personal taste will be the arbiter.

#### Parallelism
gulp flaunts its use of [orchestrator](https://www.npmjs.com/package/orchestrator) and I think, that is a great part of gulp's appeal. Grunt will get that as well at some point; when, I don't know. Until then it'll be a plus on gulp's side, but don't expect it to last.

#### Files versus Streams
Grunt reads and writes files a lot, gulp doesn't. You can set your project up in such a way as to read and write only once per task, which you cannot with Grunt! To my mind, that's a clear conceptual plus for gulp. Of course, it needs some thought to pull that off properly, but that can definitely be done. You can view a bare-bones example of how to do that in my [gulp-file-structure repository](https://github.com/rasenplanscher/gulp-file-structure).

#### Making Apple Pie with Oranges
One thing I see often, especially with people switching from Grunt to gulp, is that they treat both with the same approach. One prominent example would be [John Papa's hottowel generator](https://github.com/johnpapa/generator-hottowel) – he basically built a Gruntfile and called it a gulpfile. You *can* do such a thing, and you *can* code a Gruntfile, and you *can* make an Apple pie with oranges – *should* you do any of these? The pie maybe, the others no! If you code your Grunt, you lose its simplicity without gaining gulp's flexibility to the same extent; if you put your gulp task in a config object, you lose flexibility and actually *increase* complexity somewhat – in both cases you gain a little and lose a lot, in my opinion. So, don't do it!

## Conclusion
So, what does that all mean in the end?

Apples and oranges are good for you, and both taste radically differently. Both have their fans and you won't change either one's mind about what tastes better. On a functional level, both tools will satisfy most frontend developers fully. 

Due to using streams and, for the time being, orchestrator, I think that, technologically, gulp is the superior tool. Would I switch all projects under my purview for that? Not all at once, but gradually. 

As for taste: some like configuration, personally I like the code-thing better. That's up you!

My suggestion: try both and see for yourself. If your team has a specific preference, don't sweat it, you're covered either way.
