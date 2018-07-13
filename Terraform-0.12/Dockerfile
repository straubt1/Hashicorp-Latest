FROM golang:alpine as terraform-core
ARG TERRAFORM_REPO=https://github.com/hashicorp/terraform.git
ARG TERRAFORM_VERSION=v0.12-dev

RUN apk add --update git bash openssh zip
ENV XC_OS="linux"
ENV XC_ARCH="amd64"

WORKDIR $GOPATH/src/github.com/hashicorp/terraform
RUN git clone --branch ${TERRAFORM_VERSION} --depth 1 ${TERRAFORM_REPO} ./ && \
    /bin/bash scripts/build.sh

FROM alpine

RUN apk add --update bash ca-certificates && \
    mkdir '/terraform'
COPY --from=terraform-core /go/bin/terraform /bin/terraform

WORKDIR /terraform
ENTRYPOINT ["/bin/terraform"]
