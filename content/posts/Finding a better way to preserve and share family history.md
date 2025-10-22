---
title: Finding a better way to preserve and share family history
date: 2025-10-22
draft: false
tags:
  - GrampsWeb
categories:
  - Genealogy
---
*Or: why I started working on open-source web genealogy.*

![](https://raw.githubusercontent.com/DavidMStraub/davidmstraub.github.io/refs/heads/main/content/posts/grampsweb.jpg)

I’ve always been fascinated by family trees. My grandfather was a hobby genealogist and local historian and had researched and produced ancestor charts going back up to ten generations. Looking at the names of all those people without whom I wouldn’t exist made me curious about the life they lived. Historical events I heard about in history classes suddenly felt much more real and tangible imagining how my ancestors must have experienced them – without knowing the outcome that we often take for granted when we look at history “backwards”.

**Going digital**

I started digitizing those family trees when I was still in school, and it didn’t take long until I realized the enormous possibilities the internet offered to the hobby genealogist. It took me longer to appreciate the necessity of checking the original sources and document everything in a traceable way. (Becoming a scientist in parallel helped in that respect.)

As I collected and investigated and documented over the years, I started to worry more and more about two questions: How can I make sure all the data is still readable and usable in a generation’s time? And how can I share all the knowledge I am collecting with my relatives?

**Preserving history**

The first question naturally led me to embrace open source tools for all of my digital assets. On genealogical time scales, no software tool can be relied on to exist forever. Commercial tools can stop existing when companies go bankrupt or change priorities. Also open source tools can stop working when developers lose interest. But when open data formats are used, all information remains accessible, and files can be revived, migrated, or repurposed long after the original tool has vanished.

Gramps is an open source, cross-platform desktop family tree app that has been around since 2001 and is actively developed by a vibrant community. Using SQLite as family tree database backend, XML as import/export format, and a well-defined data model to represent genealogical information, it was exactly what I was looking for to ensure all the time I invested into documenting my research digitally wasn’t wasted.

Initially, I used Gramps only for the “family tree”, i.e. the life dates of ancestors. It took me a few years to recognize the value of going “all in”: I dumped all external note taking and documentation tools and adopted the philosophy: What’s not in my genealogical database doesn’t exist. That way, I’m ensuring that persisting this database in a readable format is all I need to do to preserve my entire research.

**Sharing results**

What was still unsolved was the second question though: how to share those results – not only to inform or to show off, but also to enable others, if they want, to conduct their own research?

My first idea was to produce a book, a family chronicle. But as I started to collect material, I realized that this book would never be finished. Genealogy is a journey, not a goal. What felt much more appropriate, given the iterative nature of genealogical research, was a blog: telling stories as they emerged from the darkness of history.

But while stories are much more accessible and interesting than pure data, the data itself – life dates, relationship charts, sources – is something I did not want to keep to myself either. Telling stories without backing them up with facts and evidence felt like a waste of time. Why would a future genealogist in two generations’ time pay any attention to them – if they even found them?

Finally, instead of a one-way communication of results, wouldn’t it make sense for an online tool to foster participation by making the genealogical research itself a collaborative effort?

**All at once**

Now all the ingredients for my ideal genealogical setup were on the table: a blog, linked with a genealogical database accessible online and containing all of the information collected inside Gramps, optionally editable by trusted individuals, of course all of it respecting data privacy by means of secure authentication.

That this mix of ingredients indeed materialized into what is now Gramps Web is thanks to circumstances and support from many sides: the fortunate fact that Gramps is written in Python, a somewhat surprising choice when it was conceived but the perfect one for building a modern web application on top of it; a break between two jobs that allowed me to invest time in a personal side project, resulting in the first prototype; and a welcoming, supportive, and collaborative Gramps open source community that embraced the project, which I am still happy to maintain today.

**Lowering the barrier**

While I was happy with the tool we had created together, many potential users struggled with the complexity of deploying a modern web application, consisting of multiple components and requiring encrypted transport for secure authentication. That’s why I launched [Grampshub](https://www.grampshub.com/) in 2023, a hosted instance of Gramps Web that can be set up within minutes, for a monthly subscription cost depending on the size of the tree.

Although the subscription model looks superficially similar to commercial genealogy platform providers, the philosophy of Grampshub is very different: while the subscription fees are necessary to cover the cloud hosting cost, Gramps Web is designed to make it as easy as possible to export *all* data inside the app, without any loss of information, and migrate to a different server, such as a self-hosted instance. Rather than tying users to a platform by locking the source evidence for their genealogical conclusions behind paywalls, it gives users the option to get started with little effort, with the freedom to move to their own server – or continue purely offline with Gramps Desktop – at any point in time.

**Wrapping up**

If you want to learn more about how Gramps Web can support you in your family history research, whether you’re a hobbyist or professional genealogist, hop over to our official documentation site, [grampsweb.org](https://www.grampsweb.org). If you happen to be a developer as well, you’ll find documentation there on how you can start contributing. There are always things to improve!
