FROM ubuntu:14.04
MAINTAINER TAGOMORI Satoshi <tagomoris@gmail.com>
LABEL Description="Fluentd docker image" Vendor="Fluent Organization" Version="1.0"

RUN apt-get update -y && apt-get install -y \
              autoconf \
              bison \
              build-essential \
              curl \      
              git \
              libffi-dev \              
              libgdbm3 \
              libgdbm-dev \
              libncurses5-dev \
              libreadline6-dev \              
              libssl-dev \
              libyaml-dev \
              zlib1g-dev \              
        && rm -rf /var/lib/apt/lists/*

# for log storage (maybe shared with host)
RUN mkdir -p /my
RUN mkdir -p /my/log
# configuration/plugins path (default: copied from .)
RUN mkdir -p /my/etc
RUN mkdir -p /my/plugins

WORKDIR /my

RUN git clone https://github.com/tagomoris/xbuild.git /my/.xbuild
RUN /my/.xbuild/ruby-install 2.2.2 /my/ruby

ENV PATH /my/ruby/bin:$PATH
RUN gem install fluentd -v 0.12.16

RUN gem install fluent-plugin-elasticsearch

ENV FLUENTD_OPT=""
ENV FLUENTD_CONF="fluent.conf"

COPY fluent.conf /
COPY agent /
COPY agent.conf /
COPY fluent.conf.erb /

EXPOSE 24224

CMD exec fluentd -c /$FLUENTD_CONF -p /my/plugins $FLUENTD_OPT
