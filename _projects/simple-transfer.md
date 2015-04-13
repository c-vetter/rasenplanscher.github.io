---
title: simple-transfer
skills:
- XHTML
- CSS
- PHP
- InkScape
links:
- "[source code](https://github.com/rasenplanscher/simple-transfer)"
- "[documentation](http://simple-transfer.rasenplanscher.info)"
---

At my first employer, we often had trouble exchanging files with our clients via email: sometimes the firewall refused the message, sometimes the attachment was deleted, sometimes the receiving client did not understand the crappy formatting of the sending client.

Instead of accepting that as inevitable, I ventured to solve the problem. I determined that having our clients download the files from us would work much better because our clients' firewalls did not filter out web links.

Services like [Dropbox](https://dropbox.com/) were not ready to serve our need yet, so I wrote a little tool that we could send files to, and which in turn would store them in a web-accessible place and return a URL for each file. It had to be simple to use, reliable, and not ugly. I achieved all of that and made both my co-workers and our clients happy.
