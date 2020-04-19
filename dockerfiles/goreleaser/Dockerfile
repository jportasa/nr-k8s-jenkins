# Based on https://github.com/goreleaser/goreleaser/blob/master/Dockerfile
FROM golang:1.14-alpine

RUN apk add -A --no-cache bash \
                       bzr \
                       curl \
                       docker-cli \
                       git \
                       rpm

RUN curl -sfL https://install.goreleaser.com/github.com/goreleaser/goreleaser.sh | sh