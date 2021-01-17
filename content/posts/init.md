---
title: "Obligatory init post"
date: 2021-01-16T12:20:32Z
draft: false
---

I have looked on to the technical blog world with a slight guilty admiration for the tech pun names that authors conjure up. Dan Abramov of React fame's [Overreacted](https://overreacted.io/), Stackoverflow team's [The Overflow](https://stackoverflow.blog/) and Github's [Changelog](https://github.blog/changelog/) being some particularly good examples. In the absence of any inspiration on my part I'll have to make do with Blog.

The domain `richardankers.co.uk` isn't a slam dunk either, I always thought I had a fairly unique last name with Ankers (thanks Mum and Dad). A quick google reveals a fantasy writer with the exact name Richard Ankers *and* an annoyingly identical middle initial M who's taken the .com domain so I'll have the .co.uk domain thanks.

For this first post I'm going to follow the format of an [Architectural Decision Records](https://github.com/joelparkerhenderson/architecture_decision_record). I quite like documenting decisions via Architectural Decision Records and for an obligatory init post discussing the contents and reasoning into committing to a blog it feels appropriate. The idea is you define a status, some context, your decision and the resulting consequences. Its the consequences bit which I think is good as you can look back at the decision two years down the line and see if things came to pass the way you thought. Its during these review session a wry smile creeps on to your face as you can see you've considered the options, understood the pitfalls and walked head first into a car crash either way.

A note on side projects - I find that some developers I follow on twitter or on blogs seem to have an almost unlimited amount of energy in realising side projects (blogs or coding efforts). If anyone cares to take a look at my [Github](https://github.com/rankers) I have a few green boxes dotted here and there each year. Fact of the matter is most stuff on my personal Github is done in my spare time with all my working time spent on work or client repositories. My goal for the first quarter of 2021 is to take a little more time for myself to realise these things including this blog. I would love to do a post every week, but in all likeliness I'll be happy with one every month or quarter or year. My thinking being nearly nothing is better that nothing.

## Status

Active

## Context (Why)

I don't expect a particularly large audience, tech blogs such as these being fairly common however I can see in others and have experienced in myself, the process of writing or presenting is a great way to cement ideas in your own head. It's that process of discussing [out loud](https://rubberduckdebugging.com/) as well as allowing public scrutiny in your thoughts which is the way you can learn in a way thats completely different to just thought alone. It's with that primary aim that I write.

### A Little About Me

I started out programming full time in 2012 after a job offer from a small VC in London. We developed using Python Django (:heart_eyes:) which was my first exposure to proper coding following university.

Following that I joined Deloitte Digital where I am today. I've developed in a load of languages and technologies including mobile apps in Objective C (:weary:) and Swift (:smile:), front ends in Javascript using React (:neutral_face:) and Angular (:neutral_face:), back ends in Python (:heart_eyes:), Node (:grinning:) and Java (:sleeping:) and a whole host of other technologies to deploy and host stuff, AWS, Azure, Teraform, Kafka (plus the other 100 technologies related to it), Bash.... the list goes on. 

On top of coding I love the process of product delivery and am fascinated by continuous integration, continuous deployment, architecture, DevOps, Lean and Agile movements. How value flows through businesses to be consumed by end users is a universal process that all companies must face into. My most recent read [Project to Product: How to Survive and Thrive in the Age of Digital Disruption with the Flow Framework](https://www.amazon.co.uk/Project-Product-Networks-Transform-Business/dp/1942788398/ref=sr_1_1?crid=3770TSEEJVEHI&dchild=1&keywords=project+to+product&qid=1610802702&sprefix=project+to+pr%2Caps%2C141&sr=8-1) by Mik Kersten touched on so many areas of product delivery in large enterprises I have to deal with at the moment. It gave a vocabulary to a number of things that had been causing me friction during my day to day work but couldn't quite label yet. I'll reserve a post to review the book in the coming months. 

Another one of those formative books you know when your reading will change how you think about your work was [Domain Driven Design (DDD)](https://www.amazon.co.uk/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_1?crid=2ASI29QXWXB7G&dchild=1&keywords=domain+driven+design&qid=1610802824&sprefix=domain+%2Caps%2C147&sr=8-1) by Eric Evans. The book is a bit dense at the beginning having to state a fair number of definitions but by the middle it starts to get into its stride. It sounds incredibly boring but the worked example on how to model paint was so simple and effective I still love wheeling it out today when discussing DDD.

If I look back over the blogs I've bookmarked I can see how my interests have evolved over time. As I switch from language to language and move from developer to senior developer to tech lead so does my reading list. I start off with bookmarks for Djangonauts and Pythonistas, then over to the Mobile (I'm not sure if other languages / communities have the same great names as the Python world maybe blog number 2 can be coming up with a load), to Javascript, to DevOps and product delivery. I also have a general legends category that are some stalwarts of the tech world I return to time and time again.

The following is a brief list of some of the things I have enjoyed reading and enjoy reading to this day:

* Pythonistas - https://kennethreitz.org/, http://nedbatchelder.com/blog/, http://www.voidspace.org.uk/, https://pydanny.com/
* Mobile - https://www.objc.io/, https://www.swiftbysundell.com/
* Javascript - Older ones such as https://johnresig.com/, https://knockoutjs.com/ (anyone remember that?) then more recent ones such as https://overreacted.io/, https://sarahdrasnerdesign.com/writing, https://css-tricks.com/archives/
* DevOps / Agile - https://continuousdelivery.com, https://trunkbaseddevelopment.com, https://dannorth.net, https://medium.com/sooner-safer-happier/, https://medium.com/forecasting-using-data, https://teamtopologies.com/
* General Legends - https://martinfowler.com/bliki/, https://blog.codinghorror.com/, https://waitbutwhy.com, https://xkcd.com/, https://news.ycombinator.com, https://hackernoon.com

### What

So onwards, now I've got my obligatory init post out the way what to discuss?

I want this blog to be a record of the work / books / technologies I'm currently interested in plus a yearly review.

I'll be delving into:

1. 
    **Engineering** - where I feel through my side projects or where through my professional work I've delved into a topic sufficiently deep enough. 
2. 
    **Architecture** - every one is striving to get this right but we all fail for some reason or    another. Not just loosely coupled but *appropriately* coupled architecture (as they say in [Evolutionary Architecture](http://evolutionaryarchitecture.com/)) is what I try to crack every time I address a design challenge.

    Kafka which enables event driven patterns is at the heart of so many architectures nowadays. The event sourcing flavour of this architectural style being one that piques my interest most. Two reasons, first being I haven't had hands on experience of it as part of my day to day work and second due to the claims it makes with respect to data management and architectural decoupling. This 7 part [blog](https://www.confluent.io/blog/data-dichotomy-rethinking-the-way-we-treat-data-and-services/) from Confluent is a fantastic introduction. We'll see over the course of the next few years if its the El Dorado of architectures it claims to be, I still have reservations with the level of complexity it introduces but there's a whole ecosystem of tooling available to abstract this away for you. I hope to experiment with this approach and firm up my thoughts through implementing it on my personal project [Racing Tips](https://github.com/racing-tips/racing-tips) which attempts to answer the age old question  - how successful are the racing tips on [Radio 4's Today programme](https://www.bbc.co.uk/programmes/b006qj9z)?

    Having spent a lot of time with Kubernetes and following the [Cloud Native Computing Foundation](https://www.cncf.io/) landscape I'm becoming more firmly in the PaaS and Serverless corner as I don't feel any one should be running Kubernetes unless you've got a shed load of people, money and time. Having said that I do love all the observability and monitoring projects that are graduating at the moment which are inevitably needed for any application.

3. 
    **Organizational Design** - more and more as I move from maker to multiplier I care about team structure. Its so related to item 2 its basically the same topic in my head now. Through Conway's law we can see Organisation design *is* software design. [Team Topologies website](https://teamtopologies.com/) and the accompanying book by Matthew Skelton and Manuel Pais is a recent read that helps square the circle with microservice and DDD as it ties architecture to the unit of delivery - the team.
4. 
    **Devops** - I love reading the State of DevOps reports each year. The 2019 [report](https://services.google.com/fh/files/misc/state-of-devops-2019.pdf) contains the following graphic which I come back to time and time again: ![alt](/images/state-of-devops-2019-metrics.png "State of DevOps") This simplicity and ubiquity of those 4 metrics is what makes them so effective. All businesses in the Digital age need to have a handle on them, everyone knows what these are and everyone can collect them with without too much specialized tooling. I still find it astounding I work in businesses that don't even attempt to collect them. On top of the State of DevOps reports I enjoy following the work of Jez Humble, Nicole Forsgren, Gene Kim, Jonathan Smart, Troy Magennis, Dan North and Dan Vacanti to mention a few.

    Special mention to Dan Vacanti and his book [Actionable Agile Metrics for Predictability](https://www.amazon.co.uk/Actionable-Agile-Metrics-Predictability-Introduction/dp/098643633X) which is one that I think is a little less well known but great at getting in to the theory of why we should work in a certain way to optimize flow (or Flow with a capital F nowadays).

5. 
    **Team Leadership** - Moving into team leadership roles as a developer comes as a shock to many including myself. No longer can you squirrel away at a computer all day cracking on with solving problems but you have to spend time reviewing, coaching, motivating and interacting with others. I love this part of my role now. I enjoy reading Pat Kua https://levelup.patkua.com/ and have recently come across the [Leadership Library for Engineers](https://leadership-library.dev) inspired by a Pat Kua workshop which collates a load of great resources.
6. 
    **Book Reviews** - Can probably see through the peppering of books mentioned in this first post I enjoy books both aligned to my job as well as for pleasure outside of work. Can see what I've been reading and what I'm planning to read on my [GoodReads](https://www.goodreads.com/review/list/128255305-richard-ankers?ref=nav_mybooks&shelf=read-professional).
7. 
    **Miscellaneous** - Any other miscellaneous topics where ever I can make a blog post.

## Consequences

Have to write something interesting now
