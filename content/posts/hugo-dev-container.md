+++
title = 'Hugo Dev Container'
date = 2024-05-07T16:14:17Z
draft = false
tags = [
    'Technology',
    'Hugo',
    'Web',
    'Reference'
]
[sitemap]
    changefreq = 'monthly'
+++
As [recently mentioned]({{< ref "embarrassment-is-a-sign-of-growth" >}}) I'm now using [Hugo](http://gohugo.io) as the technology upon which this blog is built. There are many things I like about Hugo, but one factor had been a bit annoying: To preview what my changes will end up looking like, I need access to a machine that has Hugo installed.

<!--more-->

This is all fine and dandy when I'm at my desk at home, where I do most of my writing. But I wanted the option to take this operation on the go, in case I'm somewhere with my iPad and feel an itch to write something down.

Enter: [GitHub Codespaces](https://github.com/features/codespaces). Codespaces are a relatively new feature in GitHub, that allow you to easily open up a clone of a GitHub repo inside a [Dev Container](https://containers.dev/).

With a little bit of futzing around, I was able to add the following file to the repo that contains this site:

{{< gist hanse00 84b236364612ee69be723dd6f9b67e6b >}}

And just like that, I can launch a Codespace directly from the GitHub UI, and author posts in my web browser, run the hugo commands to preview the posts, and then commit them so they get deployed to the live site.

There are a few rough edges, where clicking on links in the preview tries to load a URL relative to localhost, which won't work since my site isn't actually running *locally* to me. Perhaps that's just an error in the theme I'm using, I'm unsure for now.

All in all, it's still great compared to not having the option to author away from my desk at all. And embarassingly for Squarespace, this works *much* better than their mobile UI.