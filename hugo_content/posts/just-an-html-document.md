+++
title = 'Just an HTML Document'
date = 2024-01-23T18:03:08-08:00
draft = false
tags = [
    'Technology',
    'HTML',
    'Reference',
    'Web'
]
[sitemap]
    changefreq = 'daily'
+++
[I recently wrote]({{< ref "back-to-basics" >}}) a bit about wanting to return to tinkering with web technologies, without all of the noise that tends to get in the way in modern web development.

Given that many people aren’t familiar with web development at all, and of those who are, I suspect many of the more junior folks haven’t ever done things the “old” way, I wanted to take a moment today to describe what exactly it takes to make a web page in this manner.

<!--more-->

## HTML

HTML stands for HyperText Markup Language, all the language really is, is a definition a few special “tags” that you can write inline with the rest of your text, those tags in turn have special meanings that the web browser understands and “marks up” appropriately.

For example, the tag &lt;b&gt; in HTML means bold, inversely &lt;/b&gt; means end-of-bold. So if you wrote something like: Hey there, &lt;b&gt;how&lt;/b&gt; are you? You would specify that the word “how” is in bold. The actual tags don’t get displayed in the text, the result would look like: Hey there, **how** are you?

Of course HTML has a whole host of other tags that do all sorts of things, from inserting video to changing the color of your text, if you know the right tags, you can do just about anything. But if you’re just getting started, there isn’t all that much you have to wrap your head around to make *something* appear.

A web page with a title and a few paragraphs of text would look something like this:

```html
<h1>Philip's Web Playground</h1>
<p>
    Like many technologists, a combination of advancement in my own career and the steady evolution of the web has driven me away from interacting with web technologies as their most basic levels.
</p>
<p>
    Rather than hand crafting HTML documents, we invent increasingly more complicated contraptions with the supposed goal of easing the original task.
    These new tools and technologies have their time and place, I believe that. But I also believe that we significantly overuse them, apply them at times and in places where they do <em>not</em> belong.
</p>
<p>
    This site exists for the explicit purpose of allowing me the joy of getting back in touch with the web, getting my hands "dirty" with web technologies new and old, and exploring their application.
    There is no dogma, I am not decidedly against any particular technology, nor am I committed to using technologies simply because they are the norm.
</p>
<p>
    I hope you find some use in this page, whether it be as a concrete technical example, or simply as an object that sparks your own curiosity for the web.
</p>
```

Notable in the context of “modern” development practices: I wrote this myself, by hand. There’s no static site generator software, or other complexity involved in “generating” the HTML. I simply sat down at my editor, and wrote it.

### Technically Valid vs. Usable

Those of you who have experience developing web pages probably realized immediately that my example above is *technically* invalid. It’s true, the HTML specification sets out a bunch of rules about which tags may be used under which circumstances, and my example does not adhere to those rules.

However it’s worth understanding that over the past three decades, developers of web browsers have put in a lot of work to make sure that anything that even remotely resembles a valid HTML document will display correctly in their browser. The example I posted isn’t valid, but it *works* in every browser I’ve tried.

If you’re someone who is trying to learn web development, I strongly recommend you start by worrying about making things work. Once you have achieved something you feel good about, reformatting it to be valid is an easier fight, than worrying about a bunch of details up front you likely won’t understand.

## The Document

Alright, we have a bit of HTML written up, now what? It goes in a document. Specifically the document should have the .html file extension, but besides that there’s no black magic. Any plain text editor, such as Notepad on Windows, or TextEdit on macOS will do.

A mistake some folks make here is, you definitely do **not want** to use a Word Processor such as Microsoft Word. These applications have their own use in marking up text documents for print and display, but they embed their own additional data besides the actual text, such as font size, position on page, etc. which does not make for valid HTML. If you try to create a page in Word and then save that, you’ll have a bad time trying to make an HTML document out of it. A simple text editor is your friend.

## Hosting

Hosting is, in my opinion, the hardest part of web development to explain to people, and it’s also the source of much busywork.

In brief, the purpose of hosting your webpage is: There needs to exist some URL (address) on the web that people can go to, and when they go there, your HTML document is presented to them. For this to happen, two distinct parts need to come together, an address needs to exist that points to a web server, and the server needs to be configured to return your page whenever people connect to it.

In my case, I’ve elected to use Google Cloud Storage (GCS) as my web server, and configured a few things on the back end for that to work with the address https://playground.mallegolhansen.com. We won’t today go into how I set up that, it can get a bit technically hairy. What’s important to know is this: The setup is a one-time activity, once everything is configured, it’s just like uploading a file to Google Drive, Dropbox, or some other internet connected storage service. Whatever HTML document I upload to the storage account, is what people get presented when they go to the address.

## Updates

So how do you update the page? You modify that document you have saved, adding, removing, or modifying the text and HTML Tags. Then you sign in to the web hosting solution and upload the new version of the file. And that’s it! There’s a constant loop of making changes to the document, and uploading the new version for people to see.

Compared to the prevailing modern practices including dozens of tools you run, need to keep updated, and integrate with each other, web development really can be easy if you don’t *need* all the potential advantages the tools offer.
