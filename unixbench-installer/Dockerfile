FROM ubuntu:22.04 as downloader

RUN apt-get update && apt-get install -y git

WORKDIR /data

RUN git clone https://github.com/kdlucas/byte-unixbench.git

RUN mkdir /tmp/deps/ && apt -d -o=dir::cache=/tmp/deps/ -y install gcc make

FROM alpine:3.18 as bin

COPY --from=downloader /data/byte-unixbench/UnixBench /UnixBench

COPY --from=downloader /tmp/deps/ /deps

ENTRYPOINT [ "sh" ]
