FROM alpine:3.12

#RUN apt-get update && apt-get install -y \
#    curl

RUN apk add --no-cache curl bash

RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl \
    && chmod +x kubectl \
    && mv kubectl /usr/local/bin/kubectl