FROM golang:1.14.3-buster
ARG VERSION=3.3.1
RUN wget https://github.com/cdr/code-server/releases/download/v${VERSION}/code-server-${VERSION}-linux-amd64.tar.gz \
    && tar -xvf code-server-${VERSION}-linux-amd64.tar.gz \
    && rm code-server-${VERSION}-linux-amd64.tar.gz \
    && mv code-server-${VERSION}-linux-amd64 /code-server
RUN mkdir /project \
    && mkdir -p /code-server/data/user-data-dir \
    && mkdir -p /code-server/data/extensions-dir
ENV PASSWORD=code-server
EXPOSE 8080
VOLUME [ "/project" ]
VOLUME [ "/code-server/data" ]
WORKDIR /home/coder/project
CMD ["/code-server/code-server", "--bind-addr", "0.0.0.0:8080", "--user-data-dir","/code-server/data/user-data-dir", "--extensions-dir","/code-server/data/extensions-dir", "/project"]