FROM ghcr.io/dancemore/dancemore/df-docker/dwarffortress:sha-0c75686

ENV DFHACK_VERSION=0.47.05-r3 \
    DFHACK_ARCHIVE_NAME=dfhack-0.47.05-r3-Linux-64bit-gcc-4.8.tar.bz2 \
    DFHACK_ARCHIVE_SHA1=66f3373e23158075cc2c76e83b8b08dee5dbad85

RUN curl -LSo dfhack.tar.bz2 https://github.com/DFHack/dfhack/releases/download/${DFHACK_VERSION}/${DFHACK_ARCHIVE_NAME} \
 && echo "${DFHACK_ARCHIVE_SHA1} *dfhack.tar.bz2" | sha1sum -c \
 && tar -xjvf dfhack.tar.bz2 \
 && rm -rf dfhack.tar.bz2 stonesense hack/plugins/stonesense.plug.so \
 && echo "{\"hide\":true}" > dfhack-config/prerelease-warning.json \
 && echo "if ! setarch x86_64 -R grep -q 00040000 /proc/self/personality; then echo 'Access to the ADDR_NO_RANDOMIZE personality is required for DFHack to run.'; echo 'See https://github.com/BenLubar/df-docker#readme for details.'; exit 2; fi" > distro_fixes.sh

CMD ["./dfhack"]
