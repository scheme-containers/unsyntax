# -*- mode: dockerfile; coding: utf-8 -*-
FROM schemers/chibi:head
RUN rm /usr/local/bin/scheme-banner
RUN apt-get update && apt-get -y --no-install-recommends install \
      ca-certificates git \
      build-essential \
      autoconf automake m4 \
      git-merge-changelog help2man \
 && rm -rf /var/lib/apt/lists/*
WORKDIR /build
RUN git clone https://gitlab.com/nieper/unsyntax.git --depth 1
WORKDIR /build/unsyntax
# RUN git submodule update --init --recursive --depth 1
RUN ./bootstrap
RUN ./configure
RUN make
RUN make install
RUN ln -s unsyntax-scheme /usr/local/bin/scheme-banner
CMD ["scheme-banner"]
