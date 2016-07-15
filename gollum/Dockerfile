FROM armhf/alpine
MAINTAINER Darren Park  <sogeuni@gmail.com>

RUN set -x && \
    apk --update add bash git ruby ruby-rdoc ruby-dev build-base icu-dev zlib-dev && \
    gem install gollum gollum-rugged_adapter omniauth-google-oauth2 omnigollum omniauth --no-ri --no-rdoc && \
    apk --purge del ruby-dev build-base icu-dev zlib-dev && \
    apk add icu zlib && \
    rm -rf /var/cache/apk/*

RUN set -x && \
    addgroup gollum && \
    adduser -g "Gollum wiki" -s /bin/bash -D -h /gollum -G gollum gollum

VOLUME /wiki

EXPOSE 4567

WORKDIR /wiki
ENTRYPOINT ["gollum"]
