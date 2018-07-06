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
COPY --from=provider-azure /go/bin/terraform-provider-azurerm /bin/terraform-provider-azurerm_${PROVIDER_AZURE_VERSION}_x4