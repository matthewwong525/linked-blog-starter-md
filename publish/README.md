# Host your second brain with Next.JS

This repository is a modified version of the [blog-starter](https://github.com/vercel/next.js/tree/canary/examples/blog-starter) provided by Next.JS. Below are some added features of the [linked-blog-starter](https://github.com/matthewwong525/linked-blog-starter):
- Automatically generated backlinks and link previews
- [[works-out-of-the-box-with-markdown-files|Works out of the box]] with your markdown files
- Supports markdown & Obsidian specific markdown syntax (via [obsidian-export](https://github.com/zoni/obsidian-export))
- Highly customizable with Next.js, Tailwind v3 and React

## How to use this with Obsidian markdown files
To use this with Obsidian, you'll need to use [obsidian-export](https://github.com/zoni/obsidian-export) to [[convert-obsidian-notes-to-common-markdown|convert your obsidian notes to common markdown]] format. Once in the common markdown format, add the markdown files to the `/common_md` folder and the blog posts will be created.

If you are tired of constantly running obsidian-export and manually deploying, see how I [[deploy-obsidian-notes-with-linked-blog-starter-and-github-actions|automate this process with GitHub actions]]

## Demo

[https://linked-blog-starter.vercel.app/](https://linked-blog-starter.vercel.app/)

## Deploy your own

Deploy the example using [Vercel](https://vercel.com?utm_source=github&utm_medium=readme&utm_campaign=next-example) or preview live with [StackBlitz](https://stackblitz.com/github/matthewwong525/linked-blog-starter)

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/git/external?repository-url=https://github.com/vercel/next.js/tree/canary/examples/blog-starter&project-name=blog-starter&repository-name=blog-starter)

### Related examples
- [Fleeting Notes](https://fleetingnotes.app)

## [[install-linked-blog-starter|Installation]]
![[install-linked-blog-starter]]

# Notes
- `linked-blog-starter` uses [Tailwind CSS](https://tailwindcss.com) [(v3.0)](https://tailwindcss.com/blog/tailwindcss-v3).
- Markdown files are statically generated
- Html is generated using [generated GitHub flavoured markdown](https://github.com/sindresorhus/github-markdown-css)

