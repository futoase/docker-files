FROM ubuntu:xenial

RUN mkdir -p /home/builder
RUN useradd builder
RUN echo "builder:builder" | chpasswd
RUN chown builder:builder /home/builder
RUN chmod 0755 /home/builder
RUN usermod -s /bin/bash builder
RUN mkdir -p /code
RUN chown builder:builder /code
RUN chmod 0755 /code

RUN apt-get update
RUN apt-get install -y build-essential make autoconf automake libtool gcc g++ gperf
RUN apt-get install -y flex bison texinfo gawk ncurses-dev libexpat-dev python python-serial sed
RUN apt-get install -y git unzip libtool-bin curl wget sudo

WORKDIR /code
USER builder
RUN git clone --recursive https://github.com/pfalcon/esp-open-sdk.git

WORKDIR /code/esp-open-sdk
RUN make STANDALONE=y
