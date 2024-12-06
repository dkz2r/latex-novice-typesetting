---
title: "Introduction"
teaching: 0
exercises: 0
questions:
- "Key question: What is LaTeX used for?"
- "Key question: How can I create a new typeset document?"
objectives:
- "How to create a new LaTeX project in Overleaf."
- "Become familiar with the Overleaf ecosystem."
- "Learn what the minimum requirements for a LaTeX document are."
- "Be able to identify an element's role in a LaTeX document."
keypoints:
- "Typesetting is used in many domains to convey information in a more readable format."
- "Creating a new, minimal document requires a document declaration, a preamble, and a document body."
- "LaTeX documents consist of commands, environments, and regular text. Commands may take arguments and/or options."
---


## What is LaTeX
LaTeX is a typesetting language, useful for combining text with mathematical equations, figures,
tables, and citations, among other things.

Unlike common word processors like Microsoft Word or LibreOffice Writer, LaTex is a *markup
language*, meaning that formatting (including bold text, bullet points, and changes in font size)
is indicated by the use of commands, special characters, or *environments*.

In order to produce the actual document, this mark-up text must be *compiled*. Errors in the
mark-up can either be non-fatal, meaning the document will compile with some warnings; or fatal,
meaning the document will fail to compile.

## Our first Overleaf Project
There are several ways to write LaTeX documents, but we'll be using Overleaf, a cloud-based LaTeX
editor. This has the advantage of being accessible from any computer with an internet connection,
without the need to install any additional software. As part of the preparation for this workshop,
you should have registered for an account on Overleaf.

We'll start by creating a new, 'Blank', project in Overleaf by clicking on the large green button
that says 'New Project' in the top left corner of the screen. This will open a drop-down menu with
a number of options. We'll select 'Blank Project' from this menu. Name the project 'LaTeX Workshop'
and click 'Create'.


## The Overleaf Interface
Once the project is created, you'll see that it isn't quite blank. There are four main panels when
you open a new project in Overleaf:

- 1. The *File Navigator* on the top left, which shows all of the files in your project.
- 2. The *File Outline* on the bottom left, which shows the structure of the current file.
- 3. The *Text Editor* in the middle, where you can write your LaTeX code.
- 4. The *Preview Pane* on the right, which shows a preview of the compiled document.

You'll notice that our project isn't quite blank, as we have a file called `main.tex` open in the
text editor with some LaTeX code already written. This is a basic LaTeX document, with some of the
minimum requirements for a LaTeX document.

## Editing the Document
We can edit the `main.tex` file by clicking on it in the *File Navigator*. This will open the file
in the text editor. Let's edit some of the provided code to create our first LaTeX document.


```latex
\documentclass{article}
\usepackage[utf8]{inputenc}

\title{Irish Fairy Tales}
\author{James Stephens}

\begin{document}

\maketitle

\section{Introduction}

\end{document}
```

Commands in LaTeX are distinguished from regular text through use of a backslash `\`. Some commands
take options and/or arguments. Arguments are placed inside curly braces `{}`. Options go in square
brackets `[]`.

The `\begin{}` and `\end{}` commands delineate an *environment*. We'll see more about environments
in later episodes; for now, we'll just say that environments each have their own set of formatting
rules and purpose.

Once you're happy with the changes you've made, click the 'Recompile' button at the top of the
screen to see the changes in the preview pane. (You can also use the keyboard shortcuts
`Ctrl + Enter` or `Ctrl + s`.)

### Looking at our document
If we look at the different parts of this document, starting at the top, we see:

1. the document class declaration (this document is an article)
2. the preamble
  * a package import statement (in our case, the `inputenc` package, which allows us to use special
    characters)
  * a metadata section — this includes the title and author
3. the document body
  * the document environment `\begin{document}` statement
    * the `\maketitle` command
    * a section heading
  * the document environment `\end{document}` statement

Some of these are absolutely necessary:

* the document class declaration `\documentclass{article}`(this document is an article)
* the document environment `\begin{document}` statement
* the document environment `\end{document}` statement

Without these, the document will not compile.

### Let's make this document a bit more interesting
Now we're going to add in some dummy text to get a sense of what a more-complete document would
look like.

We'll do this using the `lipsum` package, which provides sample text blocks from a common
placeholder text.

> ## Lorem Ipsum
>
> Lorem Ipsum is a common piece of placeholder text used in publishing and graphic design. It is
> often used to demonstrate the visual form of a document without relying on meaningful content.
>
> The text itself comes from the first-century BC work *De finibus bonorum et malorum* by Marcus
> Tullius Cicero.
{: .callout}

We'll need to add a new `\usepackage{}` command, with the argument `lipsum`, to the metadata
section. Then we can add the `\lipsum` commands to the document body:


```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{lipsum}

\title{Irish Fairy Tales}
\author{James Stephens}

\begin{document}

\maketitle

\section{Introduction}
\lipsum

\end{document}
```

When we recompile the document, we'll see that the `\lipsum` command has added some dummy text to
the document body below the section heading.


> ## Challenge 1
>
> Look at the following LaTeX code and decide if it will compile as written.
> If you say no, decide why not.
>
> ```latex
> \documentclass{article}
> \usepackage[utf8]{inputenc}
>
> \title{The Playboy of the Western World}
> \author{JM Synge}
>
> \begin{document}
>
> \maketitle
>
> \section{Introduction}
>
> ```
> > ## Answer
> >
> > This code will not compile as written (or, if it does, it will throw
> > some warnings). It is missing the `\end{document}` statement.
> >
> > {: .tex}
> {: .solution}
{: .challenge}
>
>
> ## Challenge 2
>
> In the above code, which of these describes the text 'JM Synge':
>
> 1. it is a command
> 1. it is an argument
> 1. it is an option
>
> > ## Answer
> >
> > It is an argument; `\author` is a command; an option would be
> > in square brackets.
> > {: .tex}
> {: .solution}
{: .challenge}
>
> ## Challenge 3
>
> Which of these lines should not go in the document preamble?
>
> 1. `\maketitle`
> 1. `\title{R.U.R.}`
> 1. `\usepackage{graphicx}`
>
> > ## Answer
> >
> > `\maketitle` does not belong in the preamble. `\title{R.U.R.}` does,
> > because this command stores metadata about the file.
> > {: .tex}
> {: .solution}
{: .challenge}
>
> ## Challenge 4
>
> Which of these lines is optional?
>
> 1. `\begin{document}`
> 1. `\maketitle`
> 1. `\documentclass{book}`
>
> > ## Answer
> >
> > `\maketitle` is optional.
> > {: .tex}
> {: .solution}
{: .challenge}

{% include links.md %}
