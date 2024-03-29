FROM ubuntu:22.04

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y tzdata \
    && echo "Etc/UTC" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

RUN apt-get install -y wget \
    libbz2-dev \
    liblzma-dev \
    zlib1g-dev \
    libcurl4-gnutls-dev \
    libssl-dev \
    build-essential

RUN apt-get install -y python3 \
    python3-pip \
    && pip3 install pandas \ 
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENV COMPLEASM_VERSION=0.2.6

RUN wget https://github.com/huangnengCSU/compleasm/releases/download/v${COMPLEASM_VERSION}/compleasm-${COMPLEASM_VERSION}_x64-linux.tar.bz2 \
    && tar -jxvf compleasm-${COMPLEASM_VERSION}_x64-linux.tar.bz2 -C /opt/ \ 
    && rm compleasm-${COMPLEASM_VERSION}_x64-linux.tar.bz2 

ENV PATH=/opt/compleasm_kit:${PATH}

RUN compleasm.py download primates -L /opt/compleasm_kit/mb_downloads

CMD ["/bin/bash"]


