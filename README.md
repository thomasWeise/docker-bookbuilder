# [thomasWeise/docker-bookbuilder](http://hub.docker.com/r/thomasweise/docker-bookbuilder/): A Docker Container for Building Electronic Books from Pandoc Markdown

[![Docker Pulls](http://img.shields.io/docker/pulls/thomasweise/docker-bookbuilder.svg)](http://hub.docker.com/r/thomasweise/docker-bookbuilder/)
[![Docker Stars](http://img.shields.io/docker/stars/thomasweise/docker-bookbuilder.svg)](http://hub.docker.com/r/thomasweise/docker-bookbuilder/)

## 1. Introduction

This is a [docker](https://www.docker.com) container intended for building electronic books from [pandoc's markdown flavor](http://pandoc.org/MANUAL.html#pandocs-markdown) by using [pandoc](http://pandoc.org/), [`R`](http://www.r-project.org/), and [TeX Live](http://tug.org/texlive/). It has pre-installed the `R` package [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR) which provides an infrastructure and additional commands to deal with hierarchically structured books and documents.

**Please read the documentation of [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR) and [this blog post](http://iao.hfuu.edu.cn/157) regarding how to use this image as fully-automated book writing and publishing tool chain.**

## 2. Local Book Compilation

The container offers a wide variety of utils to build electronic books from markdown sources, which are all discussed in the documentation of [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR).
Here we just provide a very quick and ultra-short description about how you can run this container locally.

You can apply the [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR) package locally to a book or document you write on your computer.
In order to avoid installing all required software and even to avoid messing with `R`, you can use this [docker container](http://hub.docker.com/r/thomasweise/docker-bookbuilder/) here that we have developed for this purpose.
[Docker](https://en.wikipedia.org/wiki/Docker_(software)) is something like a light-weight virtual machine, and our container is basically a copy of a complete Linux installation with all required components that you can run on your local computer.

If you have Linux and docker installed on your system, all what it takes is the following command:

      docker run -v "INPUT_DIR":/input/ \
                 -v "OUTPUT_DIR":/output/ \
                 -e COMMIT=MY_COMMIT \
                 -e REPOSITORY=MY_REPOSITORY_NAME \
                 -t -i thomasweise/docker-bookbuilder BOOK_ROOT_MD_FILE YOUR_BOOK_OUTPUT_BASENAME

Here, it is assumed that

- `INPUT_DIR` is the directory where your book sources reside, let's say `/home/my/book/sources/`.
- `BOOK_ROOT_MD_FILE` is the root file of your book, say `book.md` (in which case, the full path of `book.md` would be `/home/my/book/sources/book.md`). Notice that you can specify only a single file, but this file can reference other files in sub-directories of `INPUT_DIR` by using commands such as  `\relative.input`.
- `OUTPUT_DIR` is the output directory where the compiled files should be placed, e.g., `/home/my/book/compiled/`. This is where the resulting files will be placed.
- `YOUR_BOOK_OUTPUT_BASENAME` is the basis for the names of the compiled files, e.g., `coolBook`, which would lead to the creation of `coolBook.pdf`, `coolBook.html`, and `coolBook.epub` in the folder references by `OUTPUT_DIR`.
- If you make use of the command  [`\meta.commit`](http://github.com/thomasWeise/bookbuildeR), you need to tell the container a commit-id. Only in this case, you need to specify the parameter "`-e COMMIT=MY_COMMIT`", where `MY_COMMIT` must be replaced with that id. Otherwise, you can leave this parameter away.
- If you make use of the command [`\meta.repository`](http://github.com/thomasWeise/bookbuildeR), you need to tell the container a commit-id. Only in this case, you need to specify the parameter "`-e REPOSITORY=MY_REPOSITORY_NAME`", where `MY_REPOSITORY_NAME` must be replaced with that id. Otherwise, you can leave this parameter away.

And that's it.
No software installation, besides docker, is required.
The container brings all required tools, scripts, packages, and what not.
Additionally, in the documentation of the [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR) package, you can find all extensions to the markdown language we introduce and how the whole build process can be automated by using continuous integration tool chains.

## 3. License

This image is licensed under the GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007, which you can find in file [LICENSE.md](http://github.com/thomasWeise/docker-bookbuilder/blob/master/LICENSE.md). The license applies to the way the image is built, while the software components inside the image are under the respective licenses chosen by their respective copyright holders.

## 4. Contact

If you have any questions or suggestions, please contact
[Prof. Dr. Thomas Weise](http://iao.hfuu.edu.cn/team/director) of the
[Institute of Applied Optimization](http://iao.hfuu.edu.cn/) at
[Hefei University](http://www.hfuu.edu.cn) in
Hefei, Anhui, China via
email to [tweise@hfuu.edu.cn](mailto:tweise@hfuu.edu.cn) and [tweise@gmx.de](mailto:tweise@gmx.de).
