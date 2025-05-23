+++
title = 'Factorio Container'
date = 2020-05-14T16:33:42-07:00
draft = false
tags = [
    'Technology',
    'Gaming',
    'Factorio',
    'Container'
]
[sitemap]
    changefreq = 'daily'
+++
A while ago I came to the realization that my Docker knowledge was rather lacking. I had heard of the tool on and off over the years, even completed the quick-start tutorials once or twice, but I had never made a container for a project of my own.

<!--more-->

Coincidentally, a group of friends were trying to organize some online gaming around the same time. We had decided that we wanted to play the excellent strategy / simulation game, [Factorio](https://factorio.com/).

A Factorio server is a simple binary that runs on Linux, but it takes a bit of setup to get right. I decided that this was the perfect candidate for me to jump into my container adventure.

The fruits of my labor are available on both [GitHub](https://github.com/Hanse00/Factorio-Container) and [Docker Hub](https://hub.docker.com/repository/docker/hanse01/factorio-container), if that’s the kind of thing that interests you.

For the rest of the article, I’m going to go into some of the struggles I had and the lessons that I learned, which may help you in your travels.

## Why?

I think it’s worth addressing the why first. Why did I make my own container, when there are already [125+ results for “factorio docker” on GitHub](https://github.com/search?q=factorio%20docker)?

There are two primary reasons:

* I wanted to learn to make my own Docker container. Regardless of if the result ends up being of value to anyone, including myself. It was a learning experience first and foremost. And I’m now comfortable saying “I know how to use Docker”, even if I’ll have to look up the details along the way.

* The most popular Docker container for Factorio out there, made by the [factoriotools team](https://github.com/factoriotools/factorio-docker), just didn’t quite work the way I wanted it to. To their defense, throughout my journey I learned that some of the reasons for that are out of their control. And in fact, my own container now has some of the same shortcomings. This just goes to show that I had things to learn about Docker.

## What?

So what exactly does the container do? On the surface it’s pretty simple.

The Factorio developers have done an amazing job supporting Linux as a first class platform, both for playing the game (Which has a native Linux client) and for hosting the headless server. So all we need to do, is download the headless server binary and run it.

As always, there are a few kinks: Making sure our container has curl for downloading the game, creating a separate user for running the server (rather than running everything as root), and perhaps the most complicated part: file permissions.

The beauty of the system, is that I can point you to my [Dockerfile](https://github.com/Hanse00/Factorio-Container/blob/master/Dockerfile) for all the exact details of the process, thereby making it self-documenting as long as you are familiar with the regular Linux commands such as apt-get, mkdir, chown, chmod, etc.

## Pain Points

Overall the process of creating a Docker container was actually surprisingly smooth. Having managed bare metal Linux servers in my past, it felt like a natural evolution.
That being said, nothing is perfect.

The one major pain point in this project, was POSIX file permissions.

 For anyone who has worked with Linux in the past, this might not come as a huge surprise, but Docker complicates this a bit. It does so by abstracting away the volume, and thereby the permissions, from where they are being used.

 For those not familiar, let’s take a step back:

 Linux and similar operating systems have a shared way of handling file permissions. At a higher level, this breaks down into: Which user owns a file / directory, which group owns a file / directory, which permissions (of a set of: read, write, and execute) does the owning user have, which permissions do members in the owning group have, and which permissions do everyone else have.

The key part in this context is the user and group who own the file / directory.

No matter what happens to the container, we want the data to stick around. That’s why Docker separates the storage of files onto a “volume” which exists independently of the container that uses it. That also means that the user on our container, which will run the application, does not exist in the context where the volume does.

### How do we work around that?

There are multiple possible solutions, but none of them feel quite as nice as I’d like.  
In the end, I decided to do exactly what the team over at factoriotools did (And so we come full circle).

To be able to configure the file permissions on the volume, we must know which UID the user on the container will have. Therefore, we set the file permissions to a specific numeric UID and configure the container user to always have that UID.  
Usually it’s considered bad practice to pin a user to a specific UID, rather than letting the system pick one at creation time, but in this case, we do not seem to have a better choice.

If you know of a more elegant way to handle file permissions in Docker volumes, I’d love to hear it!


## Lessons Learned

Although seemingly contradictory, two lessons that are important to keep in mind when starting out a project, especially in a space that’s already occupied by other projects:

* Others likely had a reason for making the choices they made.
* Just because someone else did it that way, doesn’t mean it’s the right way for you to do it.

Although in my case, I now realize why those before me picked the path that they did, however, it wasn’t obvious from the beginning that it was the right way to do it. And by not following them blindly, I learned a lot.

### Document your decisions

Although code commenting is a highly debated topic, my 2 cents are: Don’t write down what your code is doing (The code is already doing that job), write down why.
That way others will have a chance at understanding why your code does something, that doesn’t look right on the surface.

### Finish your projects

Although perhaps a bit meta, it really made a change to my mood once the project had reached my defined finish line.

I have tons of other projects I have worked on over the years, but very few have reached a true completion point.
I’m definitely going to strive to finish more projects in the future, for some definition of finish, and I recommend you do the same.
Keep in mind, finish doesn’t have to mean that you bring it to market and sell to 10 million users. Finish is whatever line you draw in the sand.
