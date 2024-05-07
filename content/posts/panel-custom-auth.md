+++
title = 'Panel Custom Auth'
date = 2024-05-06T15:44:14-07:00
draft = false
tags = [
    'Technology',
    'Python',
    'Panel',
    'Authentication',
    'Reference'
]
[sitemap]
    changefreq = 'monthly'
+++
I've recently been using the [Panel](https://panel.holoviz.org) framework on a Python project.

Deep in the bowels of the documentation, it is [mentioned](https://panel.holoviz.org/how_to/authentication/providers.html#plugins) that a custom auth plugin can be provided if a project needs to use a different authentication mechanism than those bundled with the framework, which is exactly what I needed.

<!--more-->

However between the vague docs, and the seeming lack of others actually having gone through with this option, it took me a while to figure out.

And so, as any good [netizen](https://en.wikipedia.org/wiki/Netizen) I'm here to show you how I did it.

## Solution

If you're just looking for some code you can reference, here it is.

If you'd like to learn more about how I got there, please read on.

{{< gist hanse00 9091a1deac10d3162b0e33e74cc3c1fe >}}

Note: I had to transcribe the code by hand, so be aware of potential typos.

## Commentary

As is often the case, I found it helpful to start with carefully reviewing the closest thing I could find to an existing solution.

The Panel framework ships with a set of OAuth providers, and a "Basic Auth" provider. Given that the backend I needed to authenticate against is also a plain old username/password situation, the basic auth provider was my starting point.

What didn't work for me, was that the basic auth provider allows you to configure only one set of credentials, a specific username and password combination that anything entered will be checked against.

So I went digging to figure out how exactly it was implemented.

What I found was a set [LoginHandler](https://github.com/holoviz/panel/blob/e6f658f6663b55ee9c5ecbdafd0e8235547bc5a1/panel/auth.py#L798) and [AuthProvider](https://github.com/holoviz/panel/blob/e6f658f6663b55ee9c5ecbdafd0e8235547bc5a1/panel/auth.py#L878) objects that *nearly* did what I needed. Unfortunately the aspects I needed to change weren't trivially configurable in the existing objects, so I opted to wholesale copy and modify them.[^1]

The outstanding task then was getting my panel application to actually load my auth provider. The `panel.serve` function takes opaque set of key value arguments[^2] that get passed down a rather lengthy call chain. Figuring out which of the auth related parameters would actually allow me to pass a specific object, rather than something like the name of a built-in auth provider, took a bit of spelunking with my debugger, but we got there in the end.

In the end I think the moral of that whole story is: Debuggers are invaluable. I understand it might be intimidating to figure out how to wrangle a proper debugger, especially when it seems like print statements can get you 90% of the way. But I truly believe it's a worthwhile endeavor to sit down and put a bit of effort into.

Especially when it comes to figuring out a long call chain between third party dependencies, there's really nothing like it.

[^1]: If anyone is looking for a side quest, I think it would be a great idea for the framework itself to contain versions of these objects where the authentication mechanism itself was the only thing that got plugged in, for maximum code reuse.

[^2]: I understand it's a common pattern, but I don't love it.
