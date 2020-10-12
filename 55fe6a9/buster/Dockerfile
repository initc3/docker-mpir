FROM buildpack-deps:buster

RUN apt-get update && apt-get install -y --no-install-recommends \
        texinfo \
        yasm \
	&& rm -rf /var/lib/apt/lists/*

ENV MPIR_COMMIT 55fe6a9f52ca532a611a89f67186ed915bbf1123

RUN set -ex \
        \
        && mkdir -p /usr/src/mpir \
        && git clone https://github.com/wbhart/mpir.git /usr/src/mpir \
        && cd /usr/src/mpir \
        && git checkout $MPIR_COMMIT \
	    \
        && ./autogen.sh \
        && mkdir /usr/local/mpir \
	    && ./configure --enable-cxx --prefix=/usr/local/mpir \
	    && make install \
	    && make check \
        && rm -rf /usr/src/mpir
