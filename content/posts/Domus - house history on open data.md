---
title: "Domus: house history on open data"
date: 2026-09-13
draft: false
tags:
  - Wikidata
  - OpenData
categories:
  - Genealogy
BookPostThumbnail: domus-thumb.jpg
---
[Domus](https://domus.genealogy.net) is a new web app I built for researching house history: who lived in a building, who owned it, when it was built, and how its address changed. Genealogists and local historians can record what they find, always with a source, and everything they add becomes open data that anyone can use and extend. This post describes how the project came about, what the app does, and how it is built.

<!--more-->

![Domus showing the Schumann-Haus in Leipzig](/posts/domus.jpg)

### Houses in genealogical research

Family history research usually starts with people: baptisms, marriages, and burials in parish registers. Going further, records of inheritance and property transfers lead to the houses those people lived in: who owned a building at a given time, who lived there, when it was built. I record these findings in [Gramps Web](/posts/finding-a-better-way-to-preserve-and-share-family-history/), which works well for my own research.

The history of a house, however, is relevant to many more people than the descendants of one family. Others research the same building from a different angle, and local history societies compile the same information for their village chronicles. German-speaking countries even have a long tradition of *Häuserbücher*, house-by-house histories of a town, but most of them exist only in print or as manuscripts.

There are online projects for this, but they are regional. [Haus und Hof](https://huh.oefr.at), for instance, maps house histories for Lower Austria, but neither its software nor its data are open. What I was looking for was a shared, open place for house histories, not bound to a region, where anyone can find, check, and extend what others have recorded.

### Wikidata and OpenHistoricalMap

It turned out that such a place already exists. [Wikidata](https://www.wikidata.org), the knowledge base of the Wikimedia projects, supports statements with time ranges and references. An address can be valid from one year to another, a person can be recorded as an occupant between two dates, and each of these statements can cite an archival source. Every edit is versioned and attributed, and all data is released under CC0.

Wikidata's inclusion criteria also differ from Wikipedia's. An item does not need to be notable in the encyclopedic sense; it needs to refer to a clearly identifiable entity described by serious, publicly available sources. An ordinary farmhouse documented in an archive qualifies. For Germany alone, Wikidata already contains more than 340,000 buildings, mostly from heritage registers.

[OpenHistoricalMap](https://www.openhistoricalmap.org) complements this with geometry. Like OpenStreetMap, but with a time dimension, it records building outlines with start and end dates, and these outlines can be linked to Wikidata items.

What was missing was an interface for genealogists and local historians. Wikidata's own editor is generic and powerful, but nobody should need to know property IDs and qualifiers to record who lived in a house in 1850.

### Domus

Domus fills this gap. Its map shows the buildings in Wikidata; selecting one shows its address history, residents and owners with their time ranges, construction and demolition dates, and its outlines from OpenHistoricalMap, with a time slider for buildings that changed over the years. In regions where openly licensed historical maps are available, they can be displayed as a background layer.

After logging in with a Wikimedia account, users can edit buildings and create new ones through forms that speak the language of genealogy. Every statement requires a source – a web page, an archival record with its call number, or a book – and the form cannot be submitted without one.

Domus is a project of the [Verein für Computergenealogie e.V.](https://www.compgen.de/) (CompGen), the German genealogy association I'm a member of, and runs under its domain. The code is [open source](https://github.com/compgen-ev/domus) under the MIT license.

### Without a backend

What I did not expect when I started is how far the public APIs of Wikidata and OpenHistoricalMap go. Domus is a purely static web app: the OAuth login for both projects, the map queries, and all edits run in the browser, without any backend involved.

Some things did need workarounds. To display only buildings, Domus has to know whether an item belongs to Wikidata's class hierarchy of building types, which has well over 9,000 entries. Resolving that hierarchy in a live query on every map movement was too slow, so the list of building types is precomputed and shipped with the app as a small static file.

Without a backend, Domus also holds no data of its own. Every contribution becomes part of Wikidata or OpenHistoricalMap the moment it is saved. So whoever records the history of a house with Domus is not betting on the future of the app: I plan to keep developing it, but the data stays accessible and usable with other tools either way.

### Getting involved

How much you will find on the map depends heavily on the region. Where heritage registers have been imported, it is well populated; in many villages, there is a church and little else. The easiest way to start is to look up your hometown on [domus.genealogy.net](https://domus.genealogy.net), which requires no login. If you have a documented finding about a building, you can add it with a Wikimedia account. For local history societies, a single street is a good first project.

I'd really like to hear how Domus works for you and what you're missing, whether you come from genealogy, local history, or Wikidata. Feel free to [contact me](/) directly, open an issue [on GitHub](https://github.com/compgen-ev/domus/issues), or start a discussion in the [CompGen forum](https://discourse.genealogy.net/c/compgen-projekte). The data model and the technical design are described in more detail in the [preprint](https://arxiv.org/abs/2608.12566).
