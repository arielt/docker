FROM rails:onbuild
MAINTAINER Ariel Tubaltsev

COPY agent /
COPY agent.conf /
COPY config.yml.erb /
COPY fluent-logger.yml.erb /

RUN bin/rake db:migrate RAILS_ENV=development
