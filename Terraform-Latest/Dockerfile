FROM golang:alpine as terraform-core
ARG TERRAFORM_REPO=https://github.com/hashicorp/terraform.git
ARG TERRAFORM_VERSION=master

RUN apk add --update git bash openssh zip
ENV XC_OS="linux"
ENV XC_ARCH="amd64"

WORKDIR $GOPATH/src/github.com/hashicorp/terraform
RUN git clone --branch ${TERRAFORM_VERSION} --depth 1 ${TERRAFORM_REPO} ./ && \
    /bin/bash scripts/build.sh


FROM golang:1.9.0 as provider-azure
ARG TERRAFORM_PROVIDER_AZURERM_REPO=https://github.com/terraform-providers/terraform-provider-azurerm.git
ARG TERRAFORM_PROVIDER_AZURERM_VERSION=master

WORKDIR $GOPATH/src/github.com/terraform-providers/terraform-provider-azurerm
RUN git clone --branch ${TERRAFORM_PROVIDER_AZURERM_VERSION} --depth 1 ${TERRAFORM_PROVIDER_AZURERM_REPO} ./ && \
    make build
RUN cp $GOPATH/bin/terraform-provider-azurerm /bin/terraform-provider-azurerm

FROM alpine
ARG PROVIDER_AZURE_VERSION=v1.8.0-latest

RUN apk add --update bash && \
    mkdir '/terraform'
COPY --from=terraform-core /go/bin/terraform /bin/terraform
COPY --from=provider-azure /go/bin/terraform-provider-azurerm /bin/terraform-provider-azurerm_${PROVIDER_AZURE_VERSION}_x4

WORKDIR /terraform
ENTRYPOINT ["/bin/terraform"]