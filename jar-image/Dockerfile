FROM openjdk:8u131-jdk-alpine

EXPOSE 8080

MAINTAINER Yangyang <522691592@qq.com>

LABEL io.openshift.s2i.scripts-url=image:///usr/libexec/s2i \
      io.s2i.scripts-url=image:///usr/libexec/s2i

ENV APP_ROOT=/opt/app-root \
    HOME=/opt/app-root/src \
    STI_SCRIPTS_URL=image:///usr/libexec/s2i \
    STI_SCRIPTS_PATH=/usr/libexec/s2i

WORKDIR /opt/app-root/src

RUN apk --update add \
    bash \
    && rm -rf /var/lib/apt/lists/* \
    && rm /var/cache/apk/* \
    && mkdir -p /usr/libexec/s2i \
    && mkdir -p /opt/app-root/src/.m2 \
    && mkdir -p /opt/app-root/deployed

ADD ./contrib/apache-maven-3.5.3-bin.tar.gz /usr/local/
RUN ln -sf /usr/local/apache-maven-3.5.3/bin/mvn /usr/local/bin/mvn
ADD ./contrib/settings.xml $HOME/.m2/

COPY ./s2i/bin/ /usr/libexec/s2i

CMD $STI_SCRIPTS_PATH/usage
