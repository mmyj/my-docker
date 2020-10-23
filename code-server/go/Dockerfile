FROM debian:10
ARG VERSION=3.6.0
ARG GO_VERSION=1.15.3

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

RUN wget -q -O - https://git.io/vQhTU | bash -s -- --version ${GO_VERSION} \
    && source /root/.bashrc

ENV PASSWORD=code-server
EXPOSE 8080
VOLUME [ "/project" ,"/code-server/data"]
WORKDIR /home/coder/project
CMD ["/code-server/bin/code-server", "--bind-addr", "0.0.0.0:8080", "--user-data-dir","/code-server/data/user-data-dir", "--extensions-dir","/code-server/data/extensions-dir", "/project"]
