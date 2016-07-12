FROM larmog/armhf-alpine-java:jdk-8u73
MAINTAINER Darren Park  <sogeuni@gmail.com>

ENV MAVEN_VERSION 3.3.9

RUN apk update && \
    apk upgrade && \
    apk add graphviz \
            git && \
    rm -rf /var/cache/apk/*

RUN wget http://apache.cs.utah.edu/maven/maven-3/"$MAVEN_VERSION"/binaries/apache-maven-"$MAVEN_VERSION"-bin.tar.gz -O - | tar xzv && \
    mv apache-maven-"$MAVEN_VERSION" /usr/lib/mvn

ENV JAVA=$JAVA_HOME/bin
ENV MVN_HOME=/usr/lib/mvn
ENV MVN=$MVN_HOME/bin
ENV PATH $PATH:$JAVA_HOME:$JAVA:$MVN_HOME:$MVN

WORKDIR /opt/plantuml-server
RUN git clone https://github.com/plantuml/plantuml-server.git .
RUN mvn install
RUN mvn jetty:help

EXPOSE 8080
ENTRYPOINT ["mvn", "jetty:run"]
