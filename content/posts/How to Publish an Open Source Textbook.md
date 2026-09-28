---
title: How to Publish an Open-Source Textbook
date: 2026-09-25
draft: false
tags:
  - CAD
  - AI
  - Markdown
  - Typst
categories:
  - Tools
---
Today, I published my first open-source textbook: [*CAD as Code – Parametric Modeling and Engineering with Python*](/docs/cad-as-code/). This post is not about the content of the book, but about the workflow of generating it, from idea to published PDF.

<!--more-->

## Why a textbook?

When I got tasked to redesign the course *Programming of CAx systems* at HM and decided to focus on code-based CAD, I was asked to provide literature recommendations for the module handbook. I was surprised how hard it was to find a textbook that was relevant to this topic. The open-source projects we're building on have excellent, thorough documentation, but I didn't find a self-contained, coherent document that covers everything from motivation through application.

For the first offering of the course this summer, I thus generated course materials from scratch, using my [Markdown plus Marp setup](/posts/my-new-presentation-slide-setup/) and [employing generative AI](/posts/how-i-use-generative-ai-in-teaching-prep/) to simplify and speed up the process. The interaction with the students during the course and their feedback were crucial to prepare and improve those materials. 

Since I release [all of my teaching materials](https://github.com/DavidMStraub/teaching-materials) under a permissive CC0 license, I thought about how I could make the course contents available to the wider open-source code-CAD community. The slides as such are not really suited as self-contained documentation; first of all, they are in German, which limits the possible audience; second, they are designed as supporting the course, not as a script that contains everything that is discussed.

The lack of an existing textbook on the course's topic combined with the shortcomings of the teaching slides as self-contained documentation were enough motivation for me to decide to forge them into a standalone textbook.

## Why open source?

The primary motivation for making the book open source was simple: as a proponent of open course materials and open-source software, lecturing about a topic that has open-source tools at its core, it just seemed the right way to give something back to the open-source community.

But making the entire toolchain open source is more than just licensing the book's contents permissively: by cloning the book's repository and replacing the content, it should be straightforward for anyone with basic software skills to create their own PDF textbook, without having to worry about choosing a typesetting software or creating a template.

Finally, creating a free textbook also gave me the freedom to try out AI-assisted workflows without having to worry about publishers' AI policies.

With the motivation settled, let me now sketch the setup I came up with.

## Authoring in MyST

From my older blog articles linked above you already know that I love Markdown and use it for content creation as much as I can – whether I'm writing something myself (such as this article that I'm typing in Obsidian) or using LLMs to generate or refactor content.

For the textbook, I quickly settled on the Markdown flavour [MyST](https://mystmd.org/), which “extends Markdown for technical, scientific communication and publication” – for instance, it allows adding figures, citations and footnotes in a standardized way.

The chapters are simply MyST Markdown files in a directory, which has the nice side effect that you can read text, code, and math in GitHub's Markdown preview ([example](https://github.com/DavidMStraub/cad-as-code-book/blob/main/chapters/ch06-mathematics-of-shape.md)). Just the figures don't show up there as GitHub doesn't support MyST's figure syntax.

## Typesetting with Typst

Until not too long ago, the next step in my pipeline would have been converting the Markdown to LaTeX, probably using [Pandoc](https://pandoc.org/), and typesetting the final PDF with XeLaTeX.

I've written countless documents, papers, theses with LaTeX and it has always been a love-hate relationship. I love using logical markup and lightweight editors to create print-ready – even beautiful! – documents. But LaTeX is slow, requires external packages for even basic features (did I mention package management is terrible?) and feels hopelessly obsolete. Once you've gotten used to Markdown, typing `\textbf{this}` for boldface is just painful.

Then I discovered [Typst](https://typst.app/).

Typst is a *modern*, open-source typesetting engine that gets all this right. No backslash flood, Markdown-like syntax for basic formatting, incremental compile that is *fast*, scriptability, very active development ... In short, once you've switched from LaTeX to Typst, you won't look back.

What's even better, MyST directly supports Typst as a backend, so no third party conversion tool is needed!

## Template

Now that the book had a solid technical foundation and build pipeline, I needed to make it look professional – ideally, *pretty*. For this, I needed to create a template. Obviously, I used an AI agent to iterate on this until I arrived at a version I was satisfied with.

The customized part is a Typst template that lives in the file `template.typ`. It contains colour and font styles, page geometry, styles for code snippets and figures, and the front matter definition (title page, imprint and table of contents). The companion file `template.yml` tells jtex, MyST's templating engine, which options exist in the template. The values for these options (such as the book's title, default font size, publisher name, and much more) are set in MyST's metadata file `myst.yml`.

## Repository

Finally, all the ingredients are committed to a GitHub repository which includes license files (specifying the CC-BY license), a citation file (allowing to generate a bibliography entry right from GitHub), and continuous integration workflows, which attach a PDF file to every release.

## Write your own book!

All of the code that is part of the build pipeline is released under the MIT license, so it is free for reuse, whether commercial or not. You're welcome to use it for your own textbook!

Here is how you can do it:

- Clone or fork the book's repository
- Adapt the book's contents in `/chapters` and `/figures`
- Update the metadata in `myst.yml`
- If you plan to make the book open source, make sure to adapt the license and citation files before making the repository public
- See the readme file for how to compile the book

And if you find something to improve in the pipeline, I'll be happy to accept a contribution to the repository. It's open source after all!