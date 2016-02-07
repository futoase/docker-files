FROM esp-open-sdk

USER root
RUN mkdir -p /opt/micropython
RUN chown builder:builder /opt/micropython
WORKDIR /opt/micropython

USER builder
CMD git clone https://github.com/micropython/micropython.git  && \
    cd micropython/esp8266 && \
    export PATH="/code/esp-open-sdk/xtensa-lx106-elf/bin:$PATH" && \
    echo $PATH && \
    make && \
    cp /opt/micropython/micropython/esp8266/build/firmware*.bin /opt/micropython && \
    rm -rf /opt/micropython/micropython
