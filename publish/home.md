---
title: "A Customizable Obsidian Publish alternative using Next.JS"
---
# A Customizable Obsidian Publish alternative using Next.JS

This repository is a modified version of the blog starter provided by Next.JS. Below are some added features of the [linked-blog-starter](https://github.com/matthewwong525/linked-blog-starter):
- Automatically generated backlinks and link previews
- [[works-out-of-the-box-with-markdown-files|Works out of the box]] with your markdown files (No configuration needed)
- Supports markdown & Obsidian specific markdown syntax (via [obsidian-export](https://github.com/zoni/obsidian-export))
- Embed "PreviewLinks" outside of the markdown files (See the footer in the [example](https://linked-blog-starter.vercel.app/home))
- Highly customizable with Next.js, Tailwind v3 and React

## Why I created this?
It's true that there are many Obsidian Publish alternatives, but, many of these solutions are hard to [[deploy-a-custom-linked-blog-starter|customize]], difficult to publish, and tend to [[linked-blog-starter-does-not-reinvent-wheel|reinvent the wheel]]. With this repository, I want to create a simple template that takes care of everything. Here's what the publish workflow looks like after [[publish-your-obsidian-notes-with-linked-blog-starter|setting everything up:]]

1. Write a note in `/publish` folder within Obsidian
2. Run the backup command [[connect-obsidian-vault-with-github|using the Obsidian Git plugin]]
3. Done. Your notes are published. 

## Demo
[https://linked-blog-starter.vercel.app/](https://linked-blog-starter.vercel.app/)

## Deploy your own
Only deploy through this method, if you want to get a quick server up and running. Otherwise, I'd recommend following the [[publish-your-obsidian-notes-with-linked-blog-starter|instructions to integrate this with your Obsidian Vault]].

Deploy the example using [Vercel](https://vercel.com/new/git/external?repository-url=https://github.com/matthewwong525/linked-blog-starter&project-name=linked-blog-starter&repository-name=linked-blog-starter) or preview live with [StackBlitz](https://stackblitz.com/github/matthewwong525/linked-blog-starter)

## Create a Custom Fork 
Here is an example of how I [forked this repo](https://fleetingnotes.app/) to create a landing page for [Fleeting Notes](https://www.fleetingnotes.app/). See how you can do something similar [[deploy-a-custom-linked-blog-starter|here]].
![[fn-website-demo.mov]]



