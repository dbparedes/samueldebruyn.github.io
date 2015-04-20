---
title: Using markdown to create any document (pdf, docx...)
layout: post
author: Sam
---

A few weeks ago I had to submit the contents of a GitHub repository to my teacher for grading. I wanted to use my readme.md-file while my teacher asked for a Word or a PDF document. Then I discovered this amazing program which converts Markdown to any desirable format!

Almost every programmer knows Markdown, right? The Markdown syntax is widely used on [GitHub](https://github.com/){:target="_blank"} and in [readme-files](https://github.com/github/markup/blob/master/README.md){:target="_blank"}.  Markdown was developed by [John Gruber](http://daringfireball.net/projects/markdown/){:target="_blank"} and Aaron Swartz as a tool to convert plain text files in the syntactic language with the same name to HTML.

The complete Markdown syntax and more information is available on [John Gruber's website](http://daringfireball.net/projects/markdown/syntax){:target="_blank"}.

As you've seen / will see, writing texts with Markdown is pretty easy and structured. It's quite easy to convert this text into another format than HTML. For that purpose, I've found [pandoc](http://johnmacfarlane.net/pandoc/){:target="_blank"}. Pandoc [packages are available](http://johnmacfarlane.net/pandoc/installing.html){:target="_blank"} for almost every operating system. I recommend [adding it to your path](http://geekswithblogs.net/renso/archive/2009/10/21/how-to-set-the-windows-path-in-windows-7.aspx){:target="_blank"} if the installer didn't do that automatically.

It's quite simple to start using Pandoc. They have some great documentation [available on their website](http://johnmacfarlane.net/pandoc/README.html){:target="_blank"} and basically all you have to type is the following:

{% highlight bash %}
pandoc -o thefileyouwant.ext thefileyouhave.otherext
{% endhighlight %}

The output is very clean and structured and the list of supported formats is endless. This way you can write everything in Markdown and convert your text to the desired format afterwards. I hope you'll enjoy using pandoc as much as I do!
