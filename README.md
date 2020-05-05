# pandoc-notes

A system for taking quick notes and transforming them into styled, indexed documents. Notes are taken in Markdown and converted into styled, standalone HTML5 via [Pandoc](https://github.com/jgm/pandoc). Uses the [Solarized](https://github.com/altercation/solarized) light palette for legibility and semantic highlighting.

## Usage

To use this system, one must first [install Pandoc](https://github.com/jgm/pandoc/blob/master/INSTALL.md) and download [pandoc-notes.css](pandoc-notes.css).

### Taking notes

Take notes using Markdown. If you are unfamiliar with Markdown's purpose and syntax, I recommend [The Markdown Guide](https://www.markdownguide.org/).

For proper presentation, I recommend using a YAML metadata block at the top of your Markdown document with at least a `title` field. I usually specify `title`, `subtitle`, `author`, and `date`, such as below:

````
---
title: Messiaen lecture
subtitle: Prof. G.'s lecture on Olivier Messiaen for Music History 3003
author: vinegar-tom
date: May 4, 2020
---
````

**This system is only set up for heading levels H1-H3**. Your title will be formatted as `<h1 class="title">`, and your highest level sections will also be `<h1>` elements with [automatic identifiers](https://pandoc.org/MANUAL.html#extension-auto_identifiers). If you use H4, H5, or H6, please edit the stylesheet to your preferences.

### Converting to HTML

For convenience, move or copy `pandoc-notes.css` into the same directory as your Markdown document.

Open your preferred CLI and navigate to this directory. Enter the following command, replacing `[input.md]` with the name of your document:

````
pandoc -s --toc -H pandoc-notes.css -f markdown [input.md] -t html -o output.html
````

You can optionally replace `output.html` with any filename of your choice, but you must keep the `.html` extension&mdash;or you can rename the file after the conversion. Your completed HTML document no longer needs to remain in the same directory as `pandoc-notes.css`, as the stylesheet was copied into the `<head>` element.

### Example

See [test.md](test/test.md) and [test.html](test/test.html) for examples.

## Philosophy

### Speed

Markdown allows one to take notes quickly, without worrying about the presentation of document. Many common word processors&mdash;like Microsoft Word, Apple Pages, or LibreOffice Writer&mdash;do not [separate content and presentation](https://en.wikipedia.org/wiki/Separation_of_content_and_presentation), which can often lead to distractions while writing.

### Semantics and accessibility

The `-s` and `-H` options produce a standalone document. You do not need internet access or the `pandoc-notes.css` file to view the fully formatted document in your web browser.

HTML documents have small file sizes and can be opened by any web browser, making your notes easy to share among different devices and/or with other people.

Semantic markup, such as the HTML produced by Pandoc, is often more accessible than other common document formats, like PDF or DOCX. This is particularly important for people who use screen readers.

### Legibility

I find the Solarized palette comfortable to read for long periods of time. I use the accent colors to highlight different elements of the document&mdash;such as headings, hyperlinks, and emphasized words&mdash;to aid in skimming.

## References

I learned about Pandoc's `-H` option from Martin McCallion's [Tip: using Pandoc to create truly standalone HTML files](https://devilgate.org/blog/2012/07/02/tip-using-pandoc-to-create-truly-standalone-html-files/).
