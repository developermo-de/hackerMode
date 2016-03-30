---
layout: post
title:  "Supervisor Trees - crashing without consequences"
date:   2016-03-28 21:22:00
author: self
attr: http://akmodi.com
description: "Programs that crash multiple times a second but still work fine."
categories:
- daily
---

Imagine applications that crash multiple times every second but still work just fine. This may sound like a magical scenario but you're probably actually quite familiar with this. In fact, there's an entire programming philosophy called ['let it crash' programming][let-it-crash] And as I found out today, Erlang has [Supervisor Trees][st-docs] that help handle this magic.

_Note: I'm not very familiar with distributed computing or with Erlang. This is my first real dive into this stuff. Please let me know about errors in my write-up when you see them ♥._

In regards to being familiar with crashing being fine - think of any REST API. Perhaps an issue with a specific API call causes a crash. Surely this shouldn't take down your server; there are other clients that need to make calls. Now of course servers don't crash this easily as they implement some reasonable recovery mechanism. 

Erlang's Supervisor Tree is essentially a slick implementation of such a recovery mechanism. Think of it as an exceptions implementation that works asynchronously - asynchronous exceptions. The processes in your app are monitored for failures and the relevant processes are restarted in a safe way to make sure you app doesn't crash.

This is definitely seeming interesting enough to warrant a deeper dive. Perhaps I'll revisit it for a weekly post :)

## Misc
Other articles from today that I thought were intersting

> [The power of Python List Comprehensions][misc1]

> [AUTOMATING XKCD-STYLE NARRATIVE CHARTS][misc2]

[st-docs]:http://erlang.org/doc/design_principles/sup_princ.html
[let-it-crash]:http://blogs.teamb.com/craigstuntz/2008/05/19/37819/
[misc1]: https://gist.github.com/bearfrieze/a746c6f12d8bada03589
[misc2]: https://source.opennews.org/en-US/articles/automating-xkcd-style-narrative-charts/