#
# thomasweise/docker-bookbuilder
#
# This is an image with a basic TeX Live installation,
# pandoc, and R, and my bookbuildeR R package.
# Source: https://github.com/thomasWeise/docker-bookbuilder/
# License: GNU GENERAL PUBLIC LICENSE, Version 3, 29 June 2007
# The license applies to the way the image is built, while the
# software components inside the image are under the respective
# licenses chosen by their respective copyright holders.
#
FROM thomasweise/docker-pandoc-r:1.1
MAINTAINER Thomas Weise <tweise@hfuu.edu.cn>

# do all the installation
RUN echo "Initial update." &&\
    apt-get update &&\
# install git, which we need to access code repositories
    echo "Install git." &&\
    apt-get install -f -y git &&\
    cd /tmp/ &&\
    echo "Install R-package bookbuildeR." &&\
    Rscript -e "if(!(require(\"bookbuildeR\"))) devtools::install_github(\"thomasWeise/bookbuildeR\")" &&\
    Rscript -e "if(!(require(\"bookbuildeR\"))) { q(status=1L); }" &&\
# delete not needed R stuff
    echo "Delete useless R stuff." &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/doc/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/help/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/example[s]*/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/demo/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/html/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/htmlwidgets/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/tinytest/.*" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/NEWS\.md" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/NEWS\.Rd" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/NEWS" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/AUTHORS" -delete || true) &&\
    (find $R_LIB_DIR -type f -regex "$R_LIB_DIR/[^/]+/CITATION" -delete || true) &&\
    (find $R_LIB_DIR -type f -empty -delete || true) &&\
    (find $R_LIB_DIR -type d -empty -delete || true) &&\
    (find /usr/share/R -type f -name "READM*" -delete || true) &&\
    (find /usr/share/R -type f -empty -delete || true) &&\
    (find /usr/share/R -type d -empty -delete || true) &&\
# downloading some csl files
    echo "Downloading some csl files." &&\
    curl -L --output "$PANDOC_DIR/association-for-computing-machinery.csl" http://www.zotero.org/styles/association-for-computing-machinery &&\
# the directories for input and output
    echo "Make directories for input and output." &&\
    mkdir /input/ &&\
    mkdir /output/ &&\
# cleanup
    echo "Final cleanup." &&\
    apt-get clean &&\
    rm -rf /tmp/* /var/tmp/* &&\
    rm -rf /var/lib/apt/lists/* &&\
    rm -f /etc/ssh/ssh_host_* &&\
    echo "All done."

ADD scripts /bin/

ENTRYPOINT ["/bin/main.sh"]

# the volumes for the input and output
VOLUME ["/input/", "/output/"]
