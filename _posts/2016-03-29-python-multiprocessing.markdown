---
layout: post
title:  "Python Multiprocessing: Compute on n cores to make your code n times faster"
date:   2016-03-29 23:53:00
author: self
attr: http://akmodi.com
description: "Easily scale your data concurrency performance with the number of your cores"
categories:
- daily
---

Building concurrent applications in Python is known to be challening because of how the Global Interpreter Lock works. However, TIL that building data concurrency into Python apps is ridiculously simple using [Multiprocessing][multiproc]. It's a standard library API that abstracts the use of subprocesses to get around the GIL.

Multiprocessing essentially makes it really simple to speed up any operation - that can be reduced to mapping a function on a list - by a multiple of n where n is the number of processors in your system. Here's how to use it:

~~~~~~~~
from multiprocessing import Pool

#data you want to map your function on
datalist = list(range(100))

#The function you're mapping onto a list
def operation(arg):
    return something

#using pool
with Pool(4) as p:
    p.map(operation, datalist)
~~~~~~~~
{: .language-python}

Here we've taken a list containing a 100 items and split the computation of _operation_ across four processors. This effectively makes this part of the code 4 times quicker. Check out the docs for [multiprocessing and Pool][pool] to learn more :).

If you found this interesting, I recommend this article on [threadpooling][threadpool].

>[http://jvns.ca/blog/2016/03/27/thread-pools-how-do-i-use-them/](http://jvns.ca/blog/2016/03/27/thread-pools-how-do-i-use-them/)


## Misc
Other articles from today that I thought were intersting

>[Why Alpha Go is a big deal][misc1]

>[NPM is changing unpublishing policies to prevent a repeat of last week][misc2]

[pool]:https://docs.python.org/3.5/library/multiprocessing.html#multiprocessing.pool.Pool
[multiproc]:https://docs.python.org/3.5/library/multiprocessing.html
[threadpool]:http://jvns.ca/blog/2016/03/27/thread-pools-how-do-i-use-them/
[st-docs]:http://erlang.org/doc/design_principles/sup_princ.html
[let-it-crash]:http://blogs.teamb.com/craigstuntz/2008/05/19/37819/
[source0]: http://www.nextplatform.com/2016/03/22/decade-container-control-google/
[misc1]: https://www.quantamagazine.org/20160329-why-alphago-is-really-such-a-big-deal/
[misc2]: http://blog.npmjs.org/post/141905368000/changes-to-npms-unpublish-policy