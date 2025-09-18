---
title: My new presentation slide setup
date: 2025-09-18
draft: false
tags:
  - Marp
  - Obsidian
  - Markdown
categories:
  - Tools
  - Development
---
Another small technical challenge in getting set up for teaching is finding a workflow for presentation slides, which will play a part in my mix of teaching methods.

Similarly to [my considerations about the new website](/posts/my-new-website-setup/), two important requirements are that I want to be able to use math and syntax highlighted code.

In my industry jobs, presentations were created in MS PowerPoint or Google Sheets, respectively, but especially the latter turned out to be terrible for rendering even the simplest equations.

In my former research job, I had already used text-file based presentation slides using [LaTeX beamer](https://ctan.org/pkg/beamer). I spent countless hours tweaking conference slides and aligning stuff with `\vspace` and other hacks. Not something I want return to.

A slightly better setup was one I used for teaching at TUM, when I started using Markdown for slides, but compiled them to beamer and then to PDF using the mighty [Pandoc](https://pandoc.org/).

Still, having a `Makefile` and needing to compile stuff is not very enjoyable, and since I've become a heavy [Obsidian](https://obsidian.md/) user and am also frequently leveraging the excellent Markdown capabilities of LLMs to speed up tedious tasks, I was very happy when my colleage [Jon](https://github.com/shimwell) introduced me to [Marp](https://marp.app/), the Markdown presentation ecosystem.

Marp allows to write simple slides in natural Markdown syntax, especially when using the `headingDivider` option that automatically starts new slides at heading of a given level.

Marp slides are rendered as HTML, so in a sense, there *is* a kind of compilation step, but it's *blazing* fast – absolutely no comparison to a Pandoc-beamer compilation. But what's even better is that there are excellent preview plugins for my favourite authoring tools.

[Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) makes VS Code's Markdown preview directly display the Marp slides and it auto-updates in real time as you are typing on your slides. One obvious reason why I like editing Markdown slides in VS Code is because I can use Github Copilot to help me complete stuff faster.

But there is even a [Marp plugin for Obsidian](https://github.com/samuele-cozzi/obsidian-marp-slides) which also generates an auto-updating live preview. So I can start working on a new lecture or talk directly in Obsidian, generate an outline and skeleton slides, and then jump over to VS Code when I need to.

The only final problem I had with this setup is that I didn't quite like the Marp default theme, and I wanted something branded for my new workplace. But since Marp themes are just CSS stylesheets, it wasn't hard to create my own style, and you can find it here: [hm-marp](https://github.com/DavidMStraub/hm-marp).

Putting all these puzzle pieces together, this is now my workflow for creating presentation slides:

1. Start a new note in Obsidian
2. Use [Templater](https://github.com/SilentVoid13/Templater) (command palette -> open insert template modal) to insert the slide template below
3. Start creating slides in Markdown and use the Marp plugin to preview them
4. When I feel the need to move over VS Code, execute an "Open in VS Code" [shell command](https://publish.obsidian.md/shellcommands/Index) I defined (see below) and continue working there, using Marp for VS Code to preview the slides. I can even move back and forth between the two apps without issues.
5. Once I need to export the slides to HTML, I can use the command palette of VS Code or Obsidian - both have the Marp export command predefined

The only thing that's missing is putting the files under git version control for sharing and I'm not quite sure what the most convenient workflow for that will be. Let's see how things evolve...

### Resources

**Obsidian slide template**

```markdown
---
marp: true
theme: hm
paginate: true
language: de
footer: Title – Author Name
headingDivider: 3
---
# Title

**Subtitle**

Author Name

### First Slide Title
```

**Open in VS Code shell command**

```bash
code -n --goto {{file_path:absolute}}:{{caret_position}}
```

