---
layout: workshop
title: "UoA LaTeX Workshop"
date: 2018-10-08
---

## Key Workshop Objectives
- Understand the basic structure of a Latex document
- Understand the typical Latex workflow
- Get you to a point where you feel confident using and experimenting with Latex on your own!

## Workshop Overview
- *Why* use Latex?
- *How* Latex works (and the typical workflow)
- Overleaf: What it is and why you might want to use it
- Basic Latex structure
- Working with sections, chapters etc.
- Organizing your files
- Figures
- Math Mode
- References and citations
- UoA thesis template
- Working with packages
- Handy tools and links

## Why use Latex? What's wrong with Word?
- Prevalence in academic literature
- Working with large files
- Professional looking typeset documents!
    - Equations easily in the various math modes
    - Tables, graphs and figures using `TikZ`, `PGF-Plots` vector graphics
    - Can even automatically populate these graphs and figures using your existing research data (e.g. with `csv` files)
    - Working with non-Latin scripts (Arabic, Sanskrit etc.)
- Not just used for academic literature
    - Academic journal articles, books, CVs, presentations, posters
    - Check out [the gallery here](https://www.overleaf.com/gallery/tagged/academic-journal) for all sorts of examples

## Typical Workflow
Do your writing in a Latex `.tex` file + Bibliography `.bib` file *(optional)* → Run the files through a Latex `distribution` (sometimes called a `compiler`) → Outputs a PDF

This is a different way of working to WYSIWYG editors like Microsoft Word. Some people claim this allows you to focus more on your content than its appearance. On the other hand your writing now has Latex specific commands intermingled with it.

## Latex Editors
These are what you actually do your writing in. Because Latex is written in plain text, if you wanted to (and plenty of people do) you could use a simple text editor like Notepad to do your writing, and then run the Latex `distribution` (the software that takes all your Latex files and outputs a PDF) yourself.

However, this is unnecessarily complicated and newer Latex editors provide lots of nice features like spell checking, code higlighting, and autocompletion.

You *must* have a Latex distribution installed on your computer to be able to `build` your Latex files.  [MikTeX](https://miktex.org/) and [TeX Live](https://www.tug.org/texlive/) are by far the most popular. On most Linux distributions and Mac OS Latex comes preinstalled. Then go ahead and download the editor of your choosing.

My personal recommendations for desktop Latex editors:

1. TeXstudio
2. TeXmaker
3. Texworks

However a more recent development in the Latex world is **web based** Latex editors. This is what we will be using today.

## Overleaf
Overleaf is a modern web based Latex editor that allows you to work on Latex documents anywhere in the world without needing to install any software, all you need is your browser (although you need an active Internet connection).

<img src="/assets/workshops/latex/overleaf_homepage.png" alt="Overleaf Homepage" width="40%"/>

## Basic Latex
```tex
\documentclass{article}
```

