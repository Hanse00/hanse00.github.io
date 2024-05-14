+++
title = "I'm Not Worried for My Career"
date = 2024-05-14T15:58:30Z
draft = false
tags = [
    'GenAI',
    'LLM',
    'Opinion',
    'Technology'
]
[sitemap]
    changefreq = 'monthly'
+++
In a recent conversation, someone asked me why people should bother learning to code anymore, when GenAI[^1] / LLMs[^2] can just generate code for you these days.

As the output of that conversation, this is a list of reasons why I am not worried for my career.

<!--more-->

[^1]: Generative Artificial Intelligence.
[^2]: Large Language Models.

# It's Not About Writing Code

It might sound conterintuitive to someone who doesn't work in this field, but being a software developer is largely not about *developing* software.

In other engineering diciplines, there seems to be a number of well understood and clearly distinct roles. Construction demands the input of architects, engineers, contractors, suveyors, crane operators, and a myriad of other participants.

Software is not as clear cut. I have not yet in my years on the job come across an individual whose job is strictly to write code based on plans laid by other people.

We find ourselves taking on many different roles, from sitting down with the client and trying to build an understanding of what they want the software to do, to building prototypes, to putting on the architecture hat and thinking through not just *what* to build, but *how* to build it so that it meets the needs set forth by our client.

Even **if** we conceeded that we don't need to type out the code anymore, the rest of the activities leave us with plenty to do.

# Someone Needs To Check the Work

Let's say you decide to utilize a LLM to generate some code on your behalf, rather than typing it by hand.

How confident are you that the code generated is correct?

If you're an experienced software engineer, you could look at the output, and if it's fairly simple, you could confirm its correctness at a glance. If it's more complicated, you have tools in your toolbox for that scenario too: You could write [Unit Tests](https://martinfowler.com/bliki/UnitTest.html) to confirm correctness for you.

In either case, your ability to confirm of the code does what you think it should, depends on yourself already having a mental model of how software works.

Perhaps you disagree: Why does anyone need to check the work? The software working is self-evident! If I click run, and it runs, then it works.

To that I would say: You underestimate the subtle and disasterous ways in which systems can fail, that aren't obvious. What would happen, if someone had [NULL as their license plate](https://www.wired.com/story/null-license-plate-landed-one-hacker-ticket-hell/)?

Replace "LLM" with "Stack Overflow", and you'll find that this isn't a new problem in our industry. There have always been those who tried to get away with not really knowing what they were doing.

# Who's Code Is It?

I'm definitely not a lawyer, so forgive me for any inacuracies here.

In general, in the U.S., when someone pays you to write something for them, the something you've written is now their property.

Seems simple enough. A client hires me to write an application for them, I do, I get paid, they have an app. Whatever they do from there is up to them.

They can hire me to come make modifications in the future, they can hire someone else, they can toss it asside and decide to do something else entirely.

But what if the code I *wrote* for them was never *mine* in the first place?

Legal battles are unfolding to answer questions exactly like this, [developers are suing GitHub](https://githubcopilotlitigation.com/), and [newspapers are suing OpenAI](https://www.reuters.com/legal/transactional/ny-times-sues-openai-microsoft-infringing-copyrighted-work-2023-12-27/).

What exactly the answers to these legal questions will be, I don't know. But if I was hiring people to do work for me, I'd err on the side of wanting to be confident the work actually belongs to me.

# The Computer Knows How - Not Why

Drawing another analogy to the physical world: there are [many ways to build a bridge](https://en.wikipedia.org/wiki/List_of_bridge_types). Each bridge type undoubtedly has a laundry list of pros and cons, costs, time to build, difficulty to service, ability to withstand natural disassters, and more. I'm not a civil engineer, and I have no idea how these different bridge types stack up against each other. But I mention all of this, because the same characteristics are true about software.

There are many ways to build working software, from monoliths to microservices, dynamic vs. statically linked dependencies, object oriented vs. functional. As with bridges, there are many choices to make along the way when designing software, and there is no one *correct* answer. It takes understanding the context in which you are building, to make the best possible choice.

* Are we trying to get someone out the door as fast as possible, to demo to potential investors, so that we can get money to build the *real thing* later?

* Are we building in a life-or-death scenario, where the guaranteed correctness of our software outweighs financial concerns?

* Do we anticipate that our code will be in use for months, years, or decades? The longer it is, the more likely we will need to deal with transitioning to new hardware, new maintanence staff, etc.

These and more, are the kinds of considerations that set you up to design software fit for its purpose. As it stands, there's no indication LLMs will be capable of taking on this mental labor.