---
layout: post
title:  "Using MathJax on Github Page"
categories: miscellaneous
---
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>
After some hours' tedious trying, I finally can using MathJax to write math formular correctly. 

At first, copy and paste following line to your markdown file.


    <script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=default"></script>

Then, **note that when using Github page to write formulars under MathJax, there is a little bit different from other platforms about the usage of commands \$ and $$.**

On Github Page, command *\\$\\$formular here\\$\\$* will be rendered as **inline formula**, different from mainstream markdown editors which will render the formular in a single line. If we want the formular in the middle of a line like:

$$y = x + \hat\beta \qquad(1)$$ 

we need input one blank line before and after the independent formular.