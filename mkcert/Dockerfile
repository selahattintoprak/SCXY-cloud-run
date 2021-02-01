FROM golang:1.12-alpine

WORKDIR /root/.local/share/mkcert

RUN apk --no-cache add git

RUN cd /go && \
    go get -u github.com/FiloSottile/mkcert && \
    cd src/github.com/FiloSottile/mkcert && \
    go build -o /bin/mkcert
#["$(ls -A /root/.local/share/mkcert)"] && echo "Existing Certs Found."; exit; || \
CMD mkcert -install && for i in $(echo ${DOMAIN_NAME} | sed "s/,/ /g"); \
    do mkcert $i; mkcert -pkcs12 $i; done && \
    tail -f -n0 /etc/hosts
