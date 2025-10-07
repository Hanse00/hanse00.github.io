+++
title = 'Triple Booting macOS, Ubuntu, and Windows'
date = 2020-03-20T16:15:32-07:00
draft = false
tags = [
    'Technology',
    'Apple',
    'macOS',
    'Ubuntu',
    'Windows'
]
[sitemap]
    changefreq = 'daily'
+++
Back in 2015, whilst I was still a student, I had a part time job at the educational institution I attended. As is too often the case, we had severe budgetary constraints, a lack of goodwill from upper management, and conflicting desires between the professors.

<!--more-->

Determined not to be defeated, my manager and I came up with a plan so audacious, that it might just work: We’d install macOS, Ubuntu, and Windows, all on the same physical Apple Mac mini devices. Effectively getting three computers for the cost of one, allowing every professor to have their system of choice, yet coming in at a price just low enough that we could sway the principal to give us the budget.

Whether that plan was the right choice, is a topic for another day. It seemed to be the best course of action for us to take at the time. And so we embarked on the journey.

If memory serves me right, I put down a grand total of ~300 hours on my worksheet during the course of the project. Most of which was spent researching on- and offline, getting intimately familiar with Apple’s EFI implementation (For better or worse), wiping the poor hard drive over and over again, each time learning something new that wouldn’t work. I lost count of how many times I concluded the task was impossible.

If not for [a blog post by David Lively](http://davidlively.com/notes/macbook-pro-triple-boot/)[^1], I’m confident my manager would have accepted my defeat.

By some combination of skill, luck, and trying for the umpteenth time, we did eventually get the desired result.
Looking back at it today, I’m not sure if I’m proud, or ashamed of the frankenmachine we created, but we did it. And for a few years after I left that place, it kept doing what it needed to do.

{{< figure src="IMG_20151005_182700.jpg" alt="A picture of the rEFInd boot screen, displaying the three OS logos to select which you wish to boot." caption="The end result: a boot screen where you can select which of the available OS'es you wish to load." >}}

Due to the mountain of unknowns I met when trying to solve the problem, I had decided early on that it had to be documented. If we ever did get it working, I wanted to be sure I knew how.

Recently I found that old PDF file, and was determined to share it forward. Just as David guided me on my way, I hope this can help anyone who wants to go down the same path. Keep in mind that much has changed since 2015, for one Apple introduced [the T2](https://support.apple.com/en-us/HT208862) which might just make this impossible[^2].

I also want to apologize for the numerous spelling and grammatical mistakes in the document, but as I have no access to any original material, it will have to do.

Do be warned, here be dragons.

{{< figure src="Triplebooting-Macintosh-with-OS-X-Windows-and-Ubuntu.pdf" link="Triplebooting-Macintosh-with-OS-X-Windows-and-Ubuntu.pdf" >}}

[^1]: I don’t know who this person is, but I owe them a debt of gratitude. This blog was the only semblance of help I found in my online research.

[^2]: At least without disabling various security features.
