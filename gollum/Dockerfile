FROM armhf/alpine
MAINTAINER Darren Park  <sogeuni@gmail.com>

RUN set -x && \
    apk --update add bash git ruby ruby-rdoc ruby-dev ruby-irb build-base icu-dev zlib-dev cmake && \
    gem install gollum gollum-rugged_adapter redcarpet omniauth-google-oauth2 omnigollum omniauth --no-ri --no-rdoc && \
    apk --purge del ruby-dev build-base icu-dev zlib-dev cmake && \
    apk add icu zlib && \
    rm -rf /var/cache/apk/*

RUN set -x && \
    addgroup gollum && \
    adduser -g "Gollum wiki" -s /bin/bash -D -h /gollum -G gollum gollum

# fix base_path issue
WORKDIR /usr/lib/ruby/gems/2.3.0/gems
RUN sed -i 's/\/\#{p.url_path}/\#{@wiki.base_path}\/\#{p.url_path}/g' ./gollum-lib-4.2.1/lib/gollum-lib/macro/global_toc.rb
RUN sed -i 's/\/\#{page.url_path}/\#{@wiki.base_path}\/\#{page.url_path}/g' ./gollum-lib-4.2.1/lib/gollum-lib/macro/navigation.rb
RUN sed -i 's/redirect options\[:route_prefix\]/redirect (request.script_name || '\'''\'') + options[:route_prefix]/g' ./omnigollum-0.1.4/lib/omnigollum.rb

# add redcarpet options
RUN sed -i 's/(Redcarpet::Render::HTML)/(Redcarpet::Render::HTML, autolink: true, tables: true, footnotes: true, strikethrough: true)/g' ./github-markup-1.4.0/lib/github/markup/markdown.rb

EXPOSE 4567

WORKDIR /gollum
RUN git init
ENTRYPOINT ["gollum", "--adapter", "rugged"]
