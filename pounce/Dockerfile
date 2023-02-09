FROM ubuntu:latest

RUN apt update
RUN apt install -y wget
RUN apt install -y git
RUN apt install -y make
RUN apt install -y cmake
RUN apt install -y autoconf
RUN apt install -y libtool
RUN apt install -y libssl-dev
RUN apt install -y pkg-config
RUN apt install -y wget
RUN apt install -y bmake
RUN apt install -y zlib1g-dev
RUN apt install -y libsqlite3-dev

WORKDIR /src

RUN git clone https://git.causal.agency/libretls/
RUN git clone https://git.causal.agency/scooper/
RUN git clone https://git.causal.agency/litterbox/
RUN git clone https://git.causal.agency/pounce/
RUN git clone https://github.com/kristapsdz/kcgi

WORKDIR /src/libretls
RUN autoreconf -fi
RUN ./configure
RUN make all
RUN make install

WORKDIR /src/pounce
RUN ./configure
RUN make all
RUN make install

WORKDIR /src/litterbox
RUN ./configure
RUN make all
RUN make install

WORKDIR /src/kcgi
RUN sed '/CPPFLAGS/s/#//' -i Makefile
RUN ./configure
RUN bmake
RUN bmake install

WORKDIR /src/scooper
RUN ./configure
RUN make all
RUN make install

CMD ["tail", "-f", "/dev/null"]
