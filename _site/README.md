# Clicker quiz manager

Easy way to maintain files of questions to be used as "clicker" (aka personal response) quizzes in classes. 

This package uses [Jekyll](https://jekyllrb.com/) to create a static website meant to be used in class to show questions for clickers. The site can be served locally or put on the web, including Github Pages (but this exposes the answers as well). 

You can visit a [live demo running on Github Pages](https://tobydriscoll.github.io/clicker-quiz/). 

## Features

* Each question is a simple Markdown file using [kramdown syntax](https://kramdown.gettalong.org/syntax.html). 
* Questions may be organized into chapters. 
* Any number of multiple-choice options is allowed. 
* Correct answer is revealed upon a click.
* Support for math is provided using [MathJax](https://www.mathjax.org/), including use of a macros file.

## Installation

1. [Install Jekyll](https://jekyllrb.com/docs/installation/).
1. Download the contents of this repo into a dedicated folder. 

## Usage

### Creating questions

The questions are stored in the `_questions` folder. Some examples are provided. Each question goes into one file. You can organize the files into subfolders for your own purposes, but these are essentially ignored by the final site. 

Each question must start with the following header:
```yaml
---
layout: question
chapter: Introduction
title: Frank Sinatra
---
```
(The three dashes to start and end the header are important.) Do not change the `layout` property. You can change the `chapter` and `title` to suit your purposes. The `chapter` property is used to group the questions. 

To insert LaTeX math, use \$ to enclose inline math and \$\$ to enclose displayed math. Edit the `_includes/texmacros.md` file to add your own macros to every page. 

### Update chapter list

Edit the `_config.yml` file. The only lines you need to change are

```yaml
collections:
  questions:
    output: true
    chapters:
    - Introduction
    - Next group
    - Other stuff
```
You can change, add, and remove chapters in this list. They will appear in this order in the site index. Each question's `chapter` property must match exactly a chapter in this list in order to appear in the index. Within a chapter, the ordering is lexicographical by file name. 

### Build and serve the site

Once questions and the configuration are ready, [build and serve the website](https://jekyllrb.com/docs/usage/). The typical use case is to use Jekyll to serve the site and point your browser to `localhost:4000` to use it. However, you can post the site to any server you wish, of course. 

## Customization

The file `assets/main.css` controls the appearance of everything, so that's where to make changes if you know what you're doing.