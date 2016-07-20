FROM armhf/alpine

ENV QEMU_EXECVE 1
COPY . /usr/bin


RUN [ "cross-build-start" ]

RUN apk add --update git

RUN [ "cross-build-end" ]
