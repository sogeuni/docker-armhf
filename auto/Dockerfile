FROM armhf/alpine

COPY qemu-arm /usr/bin/qemu-arm-static

RUN ["/usr/bin/qemu-arm-static", "apk", "add", "--update", "git"] 

RUN apk add --update git
