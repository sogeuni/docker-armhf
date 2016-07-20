FROM armhf/alpine

COPY qemu-arm-static /usr/bin/qemu-arm-static

#RUN ["/usr/bin/qemu-arm-static", "/bin/sh", "-c", "/bin/echo Hello from ARM container"] 
RUN echo Hello

RUN apk add --update git
