FROM alpine

ARG VERSION=v5.1.1
ARG FILENAME=oauth2_proxy-${VERSION}.linux-amd64.go1.14.2

RUN wget -q https://github.com/oauth2-proxy/oauth2-proxy/releases/download/${VERSION}/${FILENAME}.tar.gz \
 && tar xzf ${FILENAME}.tar.gz \
 && mv ${FILENAME}/oauth2_proxy /bin/ \
 && rm -rf ${FILENAME}*

CMD ["/bin/oauth2_proxy"]