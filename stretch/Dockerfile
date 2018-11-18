FROM golang:1.11.2-stretch

ENV LIBRDKAFKA_VERSION=0.11.6

RUN mkdir -p /root/librdkafka
WORKDIR /root/librdkafka

RUN wget -O "librdkafka.tar.gz" "https://github.com/edenhill/librdkafka/archive/v${LIBRDKAFKA_VERSION}.tar.gz"

RUN mkdir -p librdkafka

RUN tar \
  --extract \
  --file "librdkafka.tar.gz" \
  --directory "librdkafka" \
  --strip-components 1

RUN cd "librdkafka" && \
  ./configure --prefix=/usr && \
  make -j "$(getconf _NPROCESSORS_ONLN)" && \
  make install
