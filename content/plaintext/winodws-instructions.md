---
title: "Windows Install Instructions"
date: 2023-02-04
slug: "Winods-install"
description: "How to Install the Software on Windows"
tags: ["installation", "Windows", "LaTeX", "pandoc"]
draft: false
math: true
toc: true
---


## Windows Installation

First a moment for evangelism. Windows is far and away the most popular operating system in the world for desktops and laptops, with 76% of the [global market share](https://gs.statcounter.com/os-market-share/desktop/worldwide/#monthly-202208-202209-bar), followed by macOS (16%) and then Linux (5%). Pretty much everyone has a working familiarity with Windows, and what more it is meant to be user-friendly for the average person. But Windows offers a much more What You See Is What You Get Approach to computing. Window's user-friendliness comes at the cost of controlling every part of your operating system.

Yes, Apple products are more cost prohibitive than products that use Windows, and Linux can be intimidating as it has comparatively less support than the more popular alternatives. With those caveats, macOS and Linux (both UNIX based operating systems) are comparatively better development platforms for the kind of computing tasks we will be covering in this workshop. For one, their file structure is much more intuitive and includes fewer redundancies, so finding where to install the software we are working with is going to be achieved much quicker on macOS or Linux than on Windows. This is to say that Windows users have a few extra steps in the noble task of switching to plain text but this guide will help you every step of the way.

### LaTeX, `pandoc`, and `Git`

#### LaTeX

$\LaTeX$, typically pronounced *lay*-tek or *lah*-tex, is a program for typesetting documents developed in the late 70s. It allows you to create really pretty documents and in particular, documents that include mathematical notation, figures, and tables. It can be used to typeset pretty much anything that needs typesetting. 

LaTeX is a pretty big program (around 5GBs) so you will need sufficient space on your hard drive to accommodate it. Depending on your system you will need to navigate to the [install page](https://www.latex-project.org/get/#tex-distributions) and pick the version that is appropriate for your OS. Follow the installation instructions as you would any other program. This takes a little time due to its size.

#### `pandoc`

`pandoc` bills itself as a "universal document converter" and can be used to convert files into different formats. It was primarily developed to take documents written in [`markdown`](https://en.wikipedia.org/wiki/Markdown) and convert them into other, prettier formats. When combined with LaTeX, `pandoc` is a pretty powerful tool, and we can use it to write in `markdown` and then simultaneously convert that document into Word, PDF, Tex and HTML. It is this software that allows you to integrate your work with your colleagues that might not want to make the shift to a plain text workflow. Further, you can actually take in documents in a common format like Word and convert them to plain text.

Just like for LaTeX above, navigate to the [install page](https://pandoc.org/installing.html), and download the installer appropriate to your OS. `pandoc` is significantly smaller than LaTeX, so you should not have an issue installing it.

#### `Git` and Github

Git is a version control system which monitors a directory for changes. Think of it as the "Track Changes" option for a Word Document, but it tracks all the changes that occur to a group of files in a directory. Git is a program with a command line user interface, so you will need to know your way around a terminal to use it. It also allows you to take advantage of open source software freely available on [Github](https://github.com/).

GitHub is a website that hosts repositories of software, and if you sign up for a free account, acts like a cloud backup for your projects when they are in plaintext. All the software hosted on GitHub can be installed using `Git`, and we will use it to install the templates we are going to be using for our documents. Install `Git` [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

### Installing Document Templates

Now that you have LaTeX and `pandoc` installed you are ready to start using plain text software for your research and writing. But if you want to have nicely formatted documents that handle all the bells and whistles that you need for your scientific and social scientific writing then you need to do just a few more steps. This is the harder part of the installation process, but I will take you step by step through it.

#### What are we installing?

We are going to be installing two collections of files: the first is a set of templates that we use to take in our raw plain text files and typeset them into beautiful PDF, HTML, and (to satisfy your Word dependent colleagues) Word Documents. These templates are what `pandoc` uses to make pretty output, but the templates themselves rely upon what are called LaTeX class and style files. These are the second collection of files we are installing. A quick preview of how to use this software. When you are done writing your document, or you want to see what it ultimately will look like, you will go to your terminal and tell `pandoc` essentially "take my plain text markdown file and make it into a PDF document" by typing in a few commands. 

`pandoc` then converts the plain text data (the prose, tables, and figures you've written and created) into a PDF using LaTeX as the software to typeset it. It isn't the case that LaTeX understands what markdown is, but `pandoc` is super nifty and actually does an intermediate step that you don't see where it converts your markdown formatted plain text file into a LaTeX file before then typesetting it. Because these are, strictly speaking, two different processes which are done by two different pieces of software that are talking to one another, we need to install the templates into two different places on your computer, where LaTeX and `pandoc`, respectively, look for files. 

We are going to be installing the two collections of templates for typesetting documents from my GitHub page using `Git`. This is actually a very straight forward and easy process but feels really overwhelming at first. All you need to do is open a terminal, `cd` to the place that we want the template files to be and tell `Git` to download them. 

The first set of templates is in a repository called [pandoc-templates](https://github.com/TimothyElder/pandoc-templates) and includes the templates that take in our markdown files and convert them into LaTeX files. The second is a set of document class and style files that include all the details for how the software will typeset our documents with LaTeX. These can be found in the repository [latex-custom-kjh](https://github.com/TimothyElder/latex-custom-kjh). Finally, we will also install a template directory, [md-starter](https://github.com/TimothyElder/md-starter), which includes template markdown and `Make` files which you can use for pretty much any document. Don't worry about what these are yet, we will cover that shortly when we start using them.

Ensure that that the software you need is installed by running the following code in a terminal:

```sh
pandoc --version
latex --version
git --version
```

Each of these commands, if the software is installed, will print out version information. If you the software is not installed then your terminal will say something like `python: command not found` or `latex: command not found` which means something has gone wrong and you will have to attempt to install the software again. _**NOTE**_: Go to the appendix below for learning out how to add to your PATH variable which could solve your problem for you.

You need to make sure that you create a directory and a sub-directory the custom LaTeX templates, class and style files. Run the following code (changing the paths for your machine):

```sh
mkdir C:\texmf && mkdir C:\texmf\tex && mkdir C:\texmf\tex\latex
```

This creates a directory where you install the custom class and style files for LaTeX. With those directories made you can install the templates into their proper locations with the following code (make sure to change the paths to match your computer):

```sh
cd C:\Users\Timot\AppData\Roaming
git clone https://github.com/TimothyElder/pandoc-templates.git
ren "pandoc-templates" ".pandoc"

cd C:\texmf\tex\latex
git clone https://github.com/TimothyElder/latex-custom-te.git

cd C:\Users\Timot\Documents
git clone https://github.com/timothyelder/md-starter

```

Windows has an extra step which includes you adding a directory to your LaTeX installation so it knows where to look. To do that do the following steps:

1. Start MiKTeX Console (either find it in the Start menu or search for it in the search bar) and open the Settings page.
2. Click the Directories tab.
3. Click the Add button and browse to the texmf root directory created earlier (`C:\texmf`).

Make sure that you change all the paths to match your machine otherwise you get lots of errors and nothing will work. If you did everything above right, Congratulations! You are one step closer to making beautiful and reproducible documents in plain text.

The template and style files we installed will handle typesetting our documents so they appear the way we want, but there are a few other features of academic papers that we might want to include that requires just a few more pieces of software. For one, you will likely be mounting an argument or writing in an area of your discipline that requires you reference past works. So you will need a bibliography, and you will probably want to include tables, figures and diagrams that you will reference in the body of your text. It is a pain having to format a bibliography yourself or to number each table and figure. What more, it is particularly annoying when you decide to rearrange your paper and then have to rearrange the number of all the tables and figures in the text.

There are a few key pieces of software that Windows does not come installed with that you will need to take the extra step of installing.

### `winget` Package Manager

`winget` is a command line based package manager for Windows that helps with installing other pieces of software. It is part of App Installer which you can download and install [here](https://apps.microsoft.com/store/detail/app-installer/9NBLGGH4NNS1?hl=en-us&gl=us&rtc=1).

### Make

Make is a tool that handles the creation of files from some source material and is super helpful when you need to repetitively run the same programs in the same order over and over again, such as when you are editing and typesetting your next paper. With `winget` installed, Make is super easy to get, just run this line of code in a command prompt on your computer: 

```sh
winget install GnuWin32.Make
```

### Python

Python is a modern general computing language that is very common in the sciences and social sciences. Though we are not going to be actively using it in the working group, some of the software that we use relies upon it. It doesn't take up much space and can be downloaded and installed [here](https://www.python.org/downloads/).

Alternatively, you can install python with `winget` using the following command: 

```sh 
winget install python
```

If you do use `winget` you may have to update your PATH variable manually, so the command prompt can find it (see [appendix](#path) below).


### pandoc-xnos

[`pandoc-xnos`](https://github.com/tomduck/pandoc-fignos) is for cross-referencing figures, tables, equations, sections and pretty much anything else that can be written in a Markdown file. This helps for automatically handling the labelling of different parts of your document, so you can move the position of a figure or table or equations without having to change the reference to it in the body of your text. Install with: 

```sh
pip install pandoc-fignos pandoc-eqnos pandoc-tablenos \
            pandoc-secnos --user
```

And then use it with `--filter pandoc-xnos` as a flag for the `pandoc` command in your `Makefile` recipe. **NOTE**: Whenever using `pandoc-fignos` or `pandoc-xnos`, they need to be invoked before the `--citeproc` filter as they both use the @ symbol to identify references and they will get confused otherwise.

### Installing a Text Editor

One of the advantages of plain text is that you can open your files on any computer with the native programs installed on it from the factory. Every computer will have a basic text editor (macOS has TextEdit and Windows has Notepad) and you could do everything we are going to do in this working group with the command line and one of these text editors (in fact you could do everything just with the command line). I *highly* recommend you install a more advanced text editor to do your work in. 

There are a few excellent options to choose from including Sublime Text, Emacs, Notepad++ and RStudio. I use Microsoft's Visual Studio Code (or VS Code for short) which is particularly good and seems to be becoming the standard. The advantage to using a text editor regardless of which specific one you choose is that they highlight the syntax of whatever programming language you are writing in (including Markdown and LaTeX) enhancing the readability of your code to help writing and debugging. What more, you can typically run everything directly in the text editor so you never need to navigate away from a single window to get all your work done. You can run `R`, `python`, and keep your \LaTeX document open all at the same time toggling between the different tasks as you need.

I really think that you should use VS Code and it is what I will be using throughout the working group and so go ahead and install it [here](https://code.visualstudio.com/download). One of the nice things about VS Code is that it is *extensible* and has all sorts of extra features designed and implemented by users to help you get things done. One of the most important extensions is a LaTeX helper that we will be using when we do have to edit or write in LaTeX. After you install VS Code go ahead and install the extension [here](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop). There are also other helpful things for writing like a [spell checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker), a tool for auto-completing [citations](https://marketplace.visualstudio.com/items?itemName=notZaki.pandocciter), a word [counter](https://marketplace.visualstudio.com/items?itemName=ms-vscode.wordcount), and support for your favorite (or not so favorite) [statistical software](https://marketplace.visualstudio.com/items?itemName=REditorSupport.r). And don't worry, installing these extensions is just a matter of clicking a button.

## Adding to PATH {#path}

A lot of the work of typesetting is going to be taking place in the terminal and sometimes you will get an annoying an inexplicable error like "this software is not on the PATH" or "I can't find this software", which means that your computer is searching the location where executable programs are located (the PATH variable) but it is not finding whatever software you are telling it to run. Why this happens is a mystery. Sometimes the software has installed onto your computer, but the terminal program doesn't know where to look for where the programs are installed. I know this is a little confusing but here is a quick lesson. When you invoke a command on the terminal the first thing the computer does is check an index of the available software, which it does by examining what is called the PATH variable. If it finds whatever you are asking it to use like `pandoc` or LaTeX or R or python or whatever, it runs the command. If it doesn't find what you tell it to look for it returns an error.

Before giving up completely try updating the PATH variable so the terminal knows where the software is. Depending on what specific command line or terminal you are using the instructions are slightly different but they will be pretty portable across platforms, and operating systems. This is one of those things that you really only have to learn once and then you'll be able to improvise a lot better later. To find out where the files for a program are on macOS, run the `which` command followed by what your looking for, such as `which pandoc`, and it will print the path to where the executables of these files are installed. Sometimes the data files for a program get installed onto our computer without the PATH variable getting updated to tell the terminal that the software is installed. Check below for relevant information about how to add to the path:

### Windows

1. The first step depends on which version of Windows you're using:
  * If you're using Windows 8 or 10, press the Windows key, then search for and
    select "System (Control Panel)".
  * If you're using Windows 7, right-click the "Computer" icon on the desktop
    and click "Properties".
2. Click "Advanced system settings".
3. Click "Environment Variables".
4. Under "System Variables", find the `PATH` variable, select it, and click
   "Edit". If there is no `PATH` variable, click "New".
5. Add your directory to the beginning of the variable value followed by `;` (a
   semicolon). For example, if the value was `C:\Windows\System32`, change it to
   `C:\Users\Me\bin;C:\Windows\System32`.
6. Click "OK".
7. Restart your terminal.