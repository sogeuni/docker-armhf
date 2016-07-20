FROM armhf/alpine

COPY qemu-arm /usr/bin/qemu-arm-static

RUN ["/usr/bin/qemu-arm-static", "/bin/sh", "-c", "apk add --update git"] 
