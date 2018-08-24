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

# do all the installation
RUN export LANG=C.UTF-8 &&\
    export DEBIAN_FRONTEND=noninteractive &&\
    cd /tmp/ &&\
    apt-get clean &&\
    apt-get update &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get update &&\
    apt-get install -f -y apt-utils &&\
    apt-get install -f -y tzdata=2018d* &&\
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
                          texlive-xetex=2017.2018* \
                          zlib1g \
                          zlib1g-dev \
                          cabal-install \
                          libxml2-dev \
                          libssl-dev \
                          libcurl4-openssl-dev \
                          r-base=3.4.* \
                          r-base-dev=3.4.* &&\
    cabal update &&\
    cabal install --dependencies-only pandoc pandoc-citeproc pandoc-crossref latex-formulae-pandoc &&\
    cabal install pandoc pandoc-citeproc pandoc-crossref latex-formulae-pandoc &&\
    R_params="repos=c(\"http://cran.us.r-project.org\", \"http://cran.uk.r-project.org\",  \"http://mirrors.ustc.edu.cn/CRAN\", \"http://cran.wu.ac.at/\", \"http://cran.utstat.utoronto.ca/\", \"http://cran.rstudio.com/\", \"https://cran.uni-muenster.de/\", \"http://ftp.iitm.ac.in/cran/\"), dependencies=TRUE, clean=TRUE" &&\
    Rscript -e "update.packages(ask=FALSE, ${R_params})" &&\
    Rscript -e "if(!(require(\"callr\"))) install.packages(\"devtools\", ${R_params})" &&\
    Rscript -e "if(!(require(\"devtools\"))) install.packages(\"devtools\", ${R_params})" &&\
    Rscript -e "devtools::install_github(\"thomasWeise/bookbuildeR\")" &&\
    Rscript -e "if(!(require(\"bookbuildeR\"))) { q(-1L); }" &&\
    mkdir /work/ &&\
    apt-get purge -f -y make-doc \
                        texlive-fonts-extra-doc \
                        texlive-fonts-recommended-doc \
                        texlive-humanities-doc \
                        texlive-latex-base-doc \
                        texlive-latex-extra-doc \
                        texlive-latex-recommended-doc \
                        texlive-metapost-doc \
                        texlive-pictures-doc \
                        texlive-pstricks-doc &&\
    apt-get clean &&\
    apt-get autoclean -y &&\
    apt-get autoremove -y &&\
    apt-get clean &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_*

# the volumes for the input and output
VOLUME ["/input/", "/output/"]
