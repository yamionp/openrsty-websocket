FROM ubuntu:14.04
MAINTAINER yamionp <yami@crimsondream.jp>
RUN \
  apt-get update \
  && apt-get install -y wget git libreadline-dev libncurses5-dev libpcre3-dev libssl-dev perl make build-essential \
  && rm -rf /var/lib/apt/lists/*
RUN \
  cd /tmp \
  && wget http://openresty.org/download/ngx_openresty-1.7.10.2.tar.gz \
  && tar xzvf ngx_openresty-1.7.10.2.tar.gz \
  && cd ngx_openresty-1.7.10.2/ \
  && ./configure \
  && make \
  && make install \
  && rm -rf /tmp/ngx_openresty*
RUN \
  cd /tmp \
  && git clone https://github.com/openresty/lua-resty-websocket.git \
  && cd ./lua-resty-websocket \
  && make \
  && make install \
  && rm -rf /tmp/lua-resty-websocket


ADD nginx.conf /etc/nginx/nginx.conf
ADD websocket.html /usr/local/openresty/nginx/html/
# ENTRYPOINT /usr/sbin/nginx -g 'daemon off;' -c /etc/nginx/nginx.conf
