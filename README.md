# [thomasWeise/docker-bookbuilder](http://hub.docker.com/r/thomasweise/docker-bookbuilder/): A Docker Container for Building Electronic Books from Pandoc Markdown

[![Docker Pulls](http://img.shields.io/docker/pulls/thomasweise/docker-bookbuilder.svg)](http://hub.docker.com/r/thomasweise/docker-bookbuilder/)
[![Docker Stars](http://img.shields.io/docker/stars/thomasweise/docker-bookbuilder.svg)](http://hub.docker.com/r/thomasweise/docker-bookbuilder/)

This is a [docker](https://www.docker.com) container intended for building electronic books from [pandoc's markdown flavor](http://pandoc.org/MANUAL.html#pandocs-markdown) by using [pandoc](http://pandoc.org/), [`R`](http://www.r-project.org/), and [TeX Live](http://tug.org/texlive/). It has pre-installed the `R` package [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR) which provides an infrastructure and additional commands to deal with hierarchically structured books and documents.

**Please read the documentation of [`bookbuildeR`](http://github.com/thomasWeise/bookbuildeR) and [this blog post](http://iao.hfuu.edu.cn/157) regarding how to use this image as fully-automated book writing and publishing tool chain.**

## 1. License

### 1.1. License of the Code Provided Here

This image is licensed under the GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007, which you can find in file [LICENSE.md](http://github.com/thomasWeise/docker-bookbuilder/blob/master/LICENSE.md). The license applies to the way the image is built, while the software components inside the image are under the respective licenses chosen by their respective copyright holders.

### 1.2. Other Components Used, Licenses of Image Components

#### 1.2.1. [Wandmalfarbe/pandoc-latex-template](https://github.com/Wandmalfarbe/pandoc-latex-template)

The build process downloads and installs into the image the pandoc LaTeX template from [Wandmalfarbe/pandoc-latex-template](https://github.com/Wandmalfarbe/pandoc-latex-template) by Pascal Wgler and John MacFarlane, which is under the [BSD 3 license](https://github.com/Wandmalfarbe/pandoc-latex-template/blob/master/LICENSE). For this, the following terms hold:

    % Copyright (c) 2018, Pascal Wagler;  
    % Copyright (c) 2014--2018, John MacFarlane
    % 
    % All rights reserved.
    % 
    % Redistribution and use in source and binary forms, with or without 
    % modification, are permitted provided that the following conditions 
    % are met:
    % 
    % - Redistributions of source code must retain the above copyright 
    % notice, this list of conditions and the following disclaimer.
    % 
    % - Redistributions in binary form must reproduce the above copyright 
    % notice, this list of conditions and the following disclaimer in the 
    % documentation and/or other materials provided with the distribution.
    % 
    % - Neither the name of John MacFarlane nor the names of other 
    % contributors may be used to endorse or promote products derived 
    % from this software without specific prior written permission.
    % 
    % THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS 
    % "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT 
    % LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS 
    % FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE 
    % COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, 
    % INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
    % BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; 
    % LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER 
    % CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT 
    % LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN 
    % ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE 
    % POSSIBILITY OF SUCH DAMAGE.
    %%
    
    %%
    % For usage information and examples visit the GitHub page of this template:
    % https://github.com/Wandmalfarbe/pandoc-latex-template
    %%
    

#### 1.2.2.  [qualiacode/arabica](https://github.com/qualiacode/arabica)

The build process downloads and installs into the image the pandoc LaTeX template from [qualiacode/arabica](https://github.com/qualiacode/arabica) by Martin Maga, which is under the [MIT license](https://github.com/qualiacode/arabica/blob/master/LICENSE). For this, the following terms hold:

    MIT License
    
    Copyright (c) 2018 Martin Maga
    
    Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
    
    The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
    
    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## 2. Contact

If you have any questions or suggestions, please contact
[Prof. Dr. Thomas Weise](http://iao.hfuu.edu.cn/team/director) of the
[Institute of Applied Optimization](http://iao.hfuu.edu.cn/) at
[Hefei University](http://www.hfuu.edu.cn) in
Hefei, Anhui, China via
email to [tweise@hfuu.edu.cn](mailto:tweise@hfuu.edu.cn).
