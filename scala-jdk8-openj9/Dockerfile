FROM adoptopenjdk/openjdk8-openj9:jdk8u162-b12_openj9-0.8.0

MAINTAINER ZXJ

RUN echo 'https://mirrors.aliyun.com/alpine/v3.7/main/' > /etc/apk/repositories \
    && echo 'https://mirrors.aliyun.com/alpine/v3.7/community/' >> /etc/apk/repositories \
    && apk update \
    && apk add tzdata \
    && apk add bash \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' > /etc/timezone \
    && apk del tzdata

ENV LANG en_US.utf8

ONBUILD COPY ./target/universal/*.zip /release/

ONBUILD RUN cd /release \
    && unzip *.zip \
    && rm *.zip \
    && cd `ls`/bin \
    && ln -s `pwd`/`ls | sed -n '1p'` /entrypoint

ONBUILD CMD ["/entrypoint", "-Dconfig.resource=prod.conf", "-Dfile.encoding=UTF8"]
