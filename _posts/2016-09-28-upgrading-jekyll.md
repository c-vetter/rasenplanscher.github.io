---
title: "Upgrading to Jekyll 3.2.1"
---

Quite some time has passed and since I'll be using this again a bit, it's a good idea to first get the project running with the latest in github pages technology. The upgrade path can be succinctly summarized as: piece of cake :D

Really, despite using a Windows machine, the issues discussed in the relevant articles did not emerge. Just `bundle update` and I was golden. Or so I thought. Running `bundle exec jekyll serve` I got some strange error about missing repo metadata:

```bash
Error: No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository.
Error: Run jekyll build --trace for more information.
```

I then researched the error, tracked it down, started writing a bug report and just to be sure to have done everything, I ran `bundle exec *build* --trace --watch` although I was certain, this should not have a different result. Strangely, it had...

Of course, that was not the trigger, I said. During the testing I had changed my Gemfile and it turns out that the problem comes from the litte part starting with the comma here:

```ruby
gem 'github-pages', group: :jekyll_plugins
```

So yeah, those plugins mess with rebuilding my site :(
The offending gem is `jekyll-github-metadata`. As it turns out, this is [a known issue](https://github.com/jekyll/github-metadata/issues/74), and won't receive a fix. Just leave it out, and all is good...

Ok, I will live with that... The dude abides, as they say ;)
