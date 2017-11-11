FROM haproxy:1.5
COPY agent /
COPY agent.conf /
COPY haproxy.cfg.erb /
COPY haproxy.cfg /usr/local/etc/haproxy/haproxy.cfg

RUN apt-get update && apt-get install -y \
  ruby
