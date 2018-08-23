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

# set the R repository as environment variable
ENV R_REPO="http://cran.us.r-project.org"

# do all the installation
RUN export LANG=C.UTF-8 &&\
    apt-get clean &&\
    apt-get update &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get update &&\
# install utilities
    apt-get install -f -y apt-utils &&\
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
# install pandoc
    apt-get install -f -y pandoc=1.19.*\
                          pandoc-citeproc=0.10.* &&\
# install R
    apt-get install -f -y r-base=3.4.*\
                          r-base-dev=3.4.* &&\
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
# install necessary R packages
    R --no-save --no-environ -e "install.packages(devtools, repos='${R_REPO}')" &&\
    R --no-save --no-environ -e "install.packages(ore, repos='${R_REPO}')" &&\
    R --no-save --no-environ -e "devtools::install.github('thomasWeise/utilizeR')" &&\
# ensure that working directory exists
    mkdir /work/ &&\
# clean up all temporary files
    apt-get clean &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get clean &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_*

VOLUME ["/work/"]
