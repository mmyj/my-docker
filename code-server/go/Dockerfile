FROM golang:1.15.5-buster
ARG VERSION=3.7.4

RUN set -eux \
    && apt-get update \
    && apt-get install -y vim curl wget git \
    && rm -rf /var/lib/apt/lists/*  

RUN wget https://github.com/cdr/code-server/releases/download/v${VERSION}/code-server-${VERSION}-linux-amd64.tar.gz -O code-server.tar.gz \
    && tar -xvf code-server.tar.gz \
    && rm code-server.tar.gz \
    && mv code-server-${VERSION}-linux-amd64 /code-server
RUN mkdir /project \
    && mkdir -p /code-server/data/user-data-dir \
    && mkdir -p /code-server/data/extensions-dir

ENV PASSWORD=code-server
EXPOSE 8080
VOLUME [ "/project" ,"/code-server/data"]
WORKDIR /home/coder/project
CMD ["/code-server/bin/code-server", "--bind-addr", "0.0.0.0:8080", "--user-data-dir","/code-server/data/user-data-dir", "--extensions-dir","/code-server/data/extensions-dir", "/project"]
