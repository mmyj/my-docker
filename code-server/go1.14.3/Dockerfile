FROM golang:1.14.3-buster
RUN wget https://github.com/cdr/code-server/releases/download/3.2.0/code-server-3.2.0-linux-x86_64.tar.gz \
    && tar -xvf code-server-3.3.0-linux-x86_64.tar.gz \
    && rm code-server-3.3.0-linux-x86_64.tar.gz \
    && mv code-server-3.3.0-linux-x86_64 /code-server
RUN mkdir /project \
    && mkdir -p /code-server/data/user-data-dir \
    && mkdir -p /code-server/data/extensions-dir
ENV PASSWORD=code-server
EXPOSE 8080
VOLUME [ "/project" ]
VOLUME [ "/code-server/data" ]
WORKDIR /home/coder/project
CMD ["/code-server/code-server", "--bind-addr", "0.0.0.0:8080", "--user-data-dir","/code-server/data/user-data-dir", "--extensions-dir","/code-server/data/extensions-dir", "/project"]