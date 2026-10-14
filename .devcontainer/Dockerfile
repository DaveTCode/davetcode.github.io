FROM mcr.microsoft.com/devcontainers/base:ubuntu

ARG HUGO_VERSION=0.168.0

RUN wget -q -O /tmp/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb && \
  dpkg -i /tmp/hugo.deb && \
  rm /tmp/hugo.deb
