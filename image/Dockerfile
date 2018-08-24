#
# thomasweise/docker-bookbuilder
#
# This is an image with a basic TeX Live installation,
# pandoc, and R.
# Source: https://github.com/thomasWeise/docker-bookbuilder/
# License: GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
# The license applies to the way the image is built, while the
# software components inside the image are under the respective
# licenses chosen by their respective copyright holders.
#
FROM ubuntu:18.04
MAINTAINER Thomas Weise <tweise@ustc.edu.cn>

# set the environment with the repository list
ENV R_REPOS="c(\"http://cran.us.r-project.org\", \"http://cran.uk.r-project.org\",  \"http://mirrors.ustc.edu.cn/CRAN\", \"http://cran.wu.ac.at/\", \"http://cran.utstat.utoronto.ca/\", \"http://cran.rstudio.com/\", \"https://cran.uni-muenster.de/\", \"http://ftp.iitm.ac.in/cran/\")"

# do all the installation
RUN export LANG=C.UTF-8 &&\
    export DEBIAN_FRONTEND=noninteractive &&\
    apt-get clean &&\
    apt-get update &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get update &&\
# install utilities
    apt-get install -f -y apt-utils &&\
# install tzdata, which is needed down the line
    apt-get install -f -y tzdata=2018d* &&\
# install some nice chinese fonts
    apt-get install -f -y fonts-arphic-bkai00mp \
                          fonts-arphic-bsmi00lp \
                          fonts-arphic-gbsn00lp \
                          fonts-arphic-gkai00mp \
                          fonts-arphic-ukai \
                          fonts-arphic-uming \
                          ttf-wqy-microhei \
                          ttf-wqy-zenhei \
                          xfonts-intl-chinese \
                          xfonts-intl-chinese-big &&\
# install TeX Live and ghostscript
    apt-get install -f -y ghostscript=9.22* \
                          make=4.1* \
                          latex-cjk-common=4.8* \
                          latex-cjk-chinese=4.8* \
                          texlive-full=2017.2018* \
                          texlive-fonts-extra=2017.2018* \
                          texlive-fonts-recommended=2017.2018* \
                          texlive-lang-cjk=2017.2018* \
                          texlive-luatex=2017.2018* \
                          texlive-pstricks=2017.2018* \
                          texlive-science=2017.2018* \
                          texlive-xetex=2017.2018* &&\
# we need cabal-install from the haskell platform to install the pandoc-crossref filter
    apt-get install -f -y cabal-install &&\
    cabal update &&\
# now we can install this filter, and also pandoc, in the newest version
    cabal install pandoc pandoc-citeproc pandoc-crossref &&\
# install dependencies needed later for R
    apt-get install -f -y libxml2-dev \
                          libssl-dev \
                          libcurl4-openssl-dev &&\
# install R
    apt-get install -f -y r-base=3.4.*\
                          r-base-dev=3.4.* &&\
    cd /tmp/ &&\
# setup the R parameters for installing packages
    R_params="repos=${R_REPOS}, dependencies=TRUE, clean=TRUE" &&\
    Rscript -e "update.packages(ask=FALSE, ${R_params})" &&\
    Rscript -e "if(!(require(\"callr\"))) install.packages(\"devtools\", ${R_params})" &&\
    Rscript -e "if(!(require(\"devtools\"))) install.packages(\"devtools\", ${R_params})" &&\
# install the bookbuildeR package from http://github.com/thomasWeise/bookbuildeR
    Rscript -e "devtools::install_github(\"thomasWeise/bookbuildeR\")" &&\
# check that the required packages have actually been installed successfully
    Rscript -e "if(!(require(\"bookbuildeR\"))) { q(-1L); }" &&\
# ensure that working directory exists
    mkdir /work/ &&\
# free huge amount of unused space
    apt-get purge -f -y make-doc \
                        texlive-fonts-extra-doc \
                        texlive-fonts-recommended-doc \
                        texlive-humanities-doc \
                        texlive-latex-base-doc \
                        texlive-latex-extra-doc \
                        texlive-latex-recommended-doc \
                        texlive-metapost-doc \
                        texlive-pictures-doc \
                        texlive-pstricks-doc \
                        texlive-science-doc &&\
# clean up all temporary files
    apt-get clean &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get clean &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_*

# the volumes for the input and output
VOLUME ["/input/", "/output/"]
