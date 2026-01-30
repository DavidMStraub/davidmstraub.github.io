---
title: How I use Generative AI in Teaching Prep
date: 2026-01-30
draft: false
tags:
  - Markdown
  - AI
categories:
  - Tools
---
Facing my first semester with full teaching load, I spent quite some time thinking about the ideal toolset to streamline the preparation work. Having already switched my [website](https://davidstraub.de/posts/my-new-website-setup/) as well as my [presentation slide setup](https://davidstraub.de/posts/my-new-presentation-slide-setup/) to large language model (LLM) friendly Markdown, it was obvious from the start that I was going to experiment with generative AI (GenAI) to help prepare lecture material.

**Why use GenAI?**

But first, let's talk about the "why". Thankfully, my colleagues already provided me with lots of material for the two courses I'm teaching this semester (Python Programming and Electrical Engineering) so I didn't have to start from scratch. But as I anyway needed to go through the material in detail to familiarize myself with the topics, and made notes along the way (of course paperless and in Markdown), I felt it made sense to prepare my own lecture slides/notes and leverage GenAI to make the process more efficient.

From my experience in academia, I know what a time sink preparing technical presentation slides can be. Ahead of conferences, I used to spend way too many hours tweaking equations, text styles, and figure placement. That's not a workflow I wanted to go back to. And even though my years in industry taught me how to be efficient in preparing PowerPoint slides under time pressure, that didn't seem like a sustainable process either.

Thus, my main goal in experimenting with GenAI for teaching prep was **to spend less time on tweaking slides and have more time to think about content**. I wanted a system where high-level editorial changes – like shortening a chapter or changing a mathematical notation across twenty slides – could be handled by an assistant in seconds, rather than requiring hours of manual formatting. Achieving this required a specific technical stack.

**Setup**

The basis of my stack is the Marp-based presentation slide setup (a Markdown ecosystem that renders text into slides), which [I already discussed in a separate post](https://davidstraub.de/posts/my-new-presentation-slide-setup/). New slides are started by a level-3 heading (`###`), slide content is plain text, bullet points, tables, and mathematical formulae typed in LaTeX.

All of my lecture notes and slides reside in my Obsidian vault, but when I use GenAI, I open the file in VS Code instead, where I have configured Github's Copilot. I found that good results are only obtained with the "premium" models, in particular Claude Sonnet 4.5, for which I'm using my monthly credit that's provided for a Github Education account.

**Workflow**

Let's say we want to add another lesson to a lecture slide deck on programming. I'm using a single slide deck for the entire course, so the agent has the existing lessons as context. Opening the file in VS Code, I would prompt in agent mode something like

> Add slides for a 90-miute lesson on classes. Focus on the basics: methods, instance attributes, constructors. Do not cover inheritance. Look at existing slides to understand the style, notation, and slide length. Use short Python code blocks for examples that can be executed in a Juypter notebook. Add a relevant exercise in the end that I can implement as live coding in class; allocate 15 minutes to it. Do not add the solution to the slides.

Obviously, it takes some experimentation which prompt works for which model and which lecture topic. What I found crucial is to tell the LLM to look at existing examples and to give it instructions about the content and level of detail.

After less than a minute, the first version of the new chapter is added to the file. Typically a second, sometimes a third round of prompting is required to tweak the content, length, and level of detail. Sometimes, slides are a bit too long (the LLM can only see the source code, not the rendered slide).

Where this workflow really shines is when refactoring a course. Sometimes, looking at the generated result, I realize there is too many different concepts for the audience to swallow in the allocated time; or I realize the logical succession of explanation requires introducing an additional concept, and dropping something else instead. In this case, prompts like "Add two slides on topic X in line 12345" or "Reduce the length of section Y by 30% by reducing the level of detail" work flawlessly.

One general problem with AI agents is that they're often too opiniated and self-confident. So when I'm giving an instruction that leave room for different approaches, I typically add: "Give me options before implementing anything." This helps reduce the number of times poor choices need to be undone.

**Conclusions**

With respect to my goal of spending less time tweaking slides and more time thinking about content, the AI-powered workflow has been very successful for me. My key takeaways are:

- The more guidance in the prompt, the better. Current AI agent still think fairly "local": they are good at creating or refactoring a couple of slides, but not great at keeping consistency and a thread throughout the whole course.
- The more existing material in a certain style, the easier it is for the LLM to infer matching content.
- Tell the agent to present options before making decisions.

What's also obvious is that LLMs are best at topics that are less specialized. "Python programming" is probably one of the most rewarding topics for present models. Comparing performance in the programming course vs electrical engineering, the latter required more detailed guidance about course structure and contents to get satisfactory results.

Finally, I haven't succeeded at integrating useful graphics into the automated workflow yet, so I'm still inserting them manually. As I'm a big fan of Creative Commons, I'm using (or creating) graphics from Wikimedia Commons wherever possible. Marp's [image syntax](https://marpit.marp.app/image-syntax?id=advanced-backgrounds) makes it easy to insert images that fill a certain fraction of a slide, without interfering with the text based workflow.

**Outlook**

Now that I have a working toolbox, I can continue to explore this workflow in the next semesters. Since development in GenAI is happening at a breathtaking speed, todays's best tool might be outdated tomorrow. I haven't used the "plan" mode of Github Copilot yet, which should simplify the planning stage described above, and I also haven't tried out Claude Code yet.

Ultimately, the real benefit of these tools is that I can keep my focus on the course's content and pedagogical structure for as long as possible before the first lecture begins, without getting bogged down in the mechanics of the slides.