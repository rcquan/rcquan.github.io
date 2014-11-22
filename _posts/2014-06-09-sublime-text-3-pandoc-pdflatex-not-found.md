---
layout: post
categories: blog
tags: [fixes, sublime, pandoc, latex, html, pdflatex, MacTeX]
comments: true
title: 'Sublime Text 3: Pandoc: pdflatex not found'
---

Running on Mac OSX Mavericks 10.9.3, I encountered a problem with the 
pandoc package in Sublime Text 3 in which I could not export markdown files into pdf format. Upon execution, Sublime Text 3 would return the following error:

pandoc: pdflatex not found. pdflatex required for output.

Because I already had the MacTeX distribution installed (which contains pdflatex), I figured that the error was the result of Sublime Text 3 not being able to locate the LaTeX engine.

To resolve this error, open the user settings for the pandoc package in Sublime Text 3 and insert the following code:

```
"default":{
    "transformations:{
        "PDF": {
            "scope": {
                "text.html": "html",
                "text.html.markdown": "markdown"
            },
            "pandoc-arguments": [
                "-t", "pdf",
                "--latex-engine=/usr/texbin/pdflatex"
            ]
        }
    }
}
```

When finished, save the user settings and exit Sublime Text 3. When you return, you should be able to export markdown files to pdf using pandoc.
