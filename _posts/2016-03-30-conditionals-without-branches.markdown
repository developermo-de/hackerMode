---
layout: post
title:  "Implementing Conditionals without branches"
date:   2016-03-30 02:35:00
author: self
attr: http://akmodi.com
description: "Why branches don't have the same issues as gotos"
categories:
- daily
technologies: asm
---

Using `goto`s in code is generally accepted as terrible idea today. Why? Well because it's expected that your processor is pipelined. This means everything in the pipeline needs to be flushed when a goto is encountered. So why aren't branch statements also bad idea for the same reason? Well, assuming they're bad for the same reason, let's look at how to implement conditional logic without using branches.

Let's take this code:

~~~~~~~~
int main (int argc, char *argv[]){
	if (argc == 2)
		return 1;
	else 
		return 100;
}
~~~~~~~~
{: .language-c}

Compiling using clang with the `-S` flag makes it clear that this is how branches are handled:

~~~~~~~~
	cmpl	$2, -8(%rbp)
	jne	ret_4
	movl	$1, -4(%rbp)
	jmp	ret_def
ret_4:
	movl	$100, -4(%rbp)
ret_def:
	movl	-4(%rbp), %eax
~~~~~~~~
{: .language-asm}

We could instead do this:

~~~~~~~~
	cmpl	$2, %edi
	movl	$1, %ecx
	movl	$100, %eax
	cmovel	%ecx, %eax
	popq	%rbp
~~~~~~~~

Not a single branch statement! The exact way in which one would optimize branch statements will depend on what happens inside your conditionals. It may be bit manipulation, it may be flag checking (like in this example), or a multitude of different things. And yes, you could build your C programs in this manner. 

But before we go around writing our programs in this ugly manner, let's reconsider our assumption: **are branches bad for the same reason gotos are**?

Turns out **they're not**. It's because of how amazing branch prediction has become. Processors are almost never resigned to flushing the pipeline because of a branch. In-fact, it may turn out that our optimized code runs slower on most processors. So writing conditionals without branches may be a neat party trick but it isn't a very useful one. 

The point of this post was twofold:
 
 1. To point out that conditionals can be implemented without branches.
 2. To remind you of how awesome processors are today.

## Misc
Other articles I enjoyed today.

>[Ubuntu on Windows? What's really going on?][misc1]

>[Defending the future from the present - EFF vs W3C][misc2]

[misc1]: http://blog.dustinkirkland.com/2016/03/ubuntu-on-windows.html
[misc2]: https://www.eff.org/deeplinks/2016/03/interoperability-and-w3c-defending-future-present
