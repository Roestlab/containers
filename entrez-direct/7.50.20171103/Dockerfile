################## BASE IMAGE ######################
FROM biocontainers/biocontainers:latest

################## METADATA ######################
LABEL base.image="biocontainers:latest"
LABEL version="3"
LABEL software="entrez-direct"
LABEL software.version="7.50.20171103"
LABEL description="Entrez Direct (EDirect) is an advanced method for accessing the NCBI's set of interconnected Entrez databases"
LABEL website="https://github.com/ncbi/magicblast"
LABEL documentation="https://ncbi.github.io/magicblast/"
LABEL License_file = "https://ncbi.github.io/magicblast/"
LABEL tags="BLAST"

################## MAINTAINER ######################
MAINTAINER Roberto Vera Alvarez <r78v10a07@gmail.com>

################## INSTALLATION ######################
USER root

ENV ZIP=edirect-7.50.20171103.tar.gz
ENV URL=ftp://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/versions/7.50.20171103/
ENV FOLDER=edirect
ENV INSTALL_FOLDER=/home/biodocker/
ENV DST=/tmp

RUN apt-get update && \
    apt-get install -y \
      liblwp-protocol-https-perl && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

USER biodocker

RUN cd $DST && \
	wget $URL/$ZIP -O $DST/$ZIP && \
	tar xzfv $DST/$ZIP -C $DST && \
	mv $DST/$FOLDER/* /home/biodocker/bin/ && \
	rm -rf $DST/$FOLDER

WORKDIR /data/

CMD ["esearch"]
