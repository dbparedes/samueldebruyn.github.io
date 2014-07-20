---
author: Sam
comments: true
date: 2014-02-10 18:49:29+00:00
layout: post
slug: using-markdown-to-create-any-document
title: Using markdown to create any document (pdf, docx...)
wordpress_id: 99
categories:
- office
---

A few weeks ago I had to submit the contents of a GitHub repository to my teacher for grading. I wanted to use my readme.md-file while my teacher asked for a Word or a PDF document. Then I discovered this amazing program which converts Markdown to any desirable format!<!-- more -->

Almost every programmer knows Markdown, right? The Markdown syntax is widely used on [GitHub ](https://github.com/)and in [readme-files](https://github.com/github/markup/blob/master/README.md).  Markdown was developed by [John Gruber](http://daringfireball.net/projects/markdown/) and [Aaron Swartz](http://www.aaronsw.com/weblog/001189) as a tool to convert plain text files in the syntactic language with the same name to HTML.

The complete Markdown syntax and more information is available on [John Gruber's website](http://daringfireball.net/projects/markdown/syntax).

As you've seen / will see, writing texts with Markdown is pretty easy and structured. It's quite easy to convert this text into another format than HTML. For that purpose, I've found [pandoc](http://johnmacfarlane.net/pandoc/). Pandoc [packages are available](http://johnmacfarlane.net/pandoc/installing.html) for almost every operating system. I recommend [adding it to your path](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx) if the installer didn't do that automatically.

It's quite simple to start using Pandoc. They have some great documentation [available on their website](http://johnmacfarlane.net/pandoc/README.html) and basically all you have to type is the following:

[code]pandoc -o thefileyouwant.ext thefileyouhave.otherext[/code]

The output is very clean and structured and the list of supported formats is endless. This way you can write everything in Markdown and convert your text to the desired format afterwards. I hope you'll enjoy using pandoc as much as I do!
