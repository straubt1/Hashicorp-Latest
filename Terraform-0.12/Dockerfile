FROM ubuntu:18.04
ARG XC_OS="linux"
ARG XC_ARCH="amd64"
ARG TERRAFORM_VERSION="0.12.0-beta1"
ARG TERRAFORM_ARCHIVE="https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_${XC_OS}_${XC_ARCH}.zip"
ARG AZURERM_VERSION="1.23.0-dev20190216H00-dev"
ARG AZURERM_ARCHIVE="http://terraform-0.12.0-dev-snapshots.s3-website-us-west-2.amazonaws.com/terraform-provider-azurerm/${AZURERM_VERSION}/terraform-provider-azurerm_${AZURERM_VERSION}_${XC_OS}_${XC_ARCH}.zip"

ARG RANDOM_VERSION="3.0.0-dev20190216H01-dev"
ARG RANDOM_ARCHIVE="http://terraform-0.12.0-dev-snapshots.s3-website-us-west-2.amazonaws.com/terraform-provider-random/${RANDOM_VERSION}/terraform-provider-random_${RANDOM_VERSION}_${XC_OS}_${XC_ARCH}.zip"
ARG TEMPLATE_VERSION="2.1.0-dev20190216H00-dev"
ARG TEMPLATE_ARCHIVE="http://terraform-0.12.0-dev-snapshots.s3-website-us-west-2.amazonaws.com/terraform-provider-template/${TEMPLATE_VERSION}/terraform-provider-template_${TEMPLATE_VERSION}_${XC_OS}_${XC_ARCH}.zip"


RUN apt-get update && apt-get -y install bash zip curl && \ 
    mkdir '/terraform'
RUN curl -o /tmp/tf012.zip ${TERRAFORM_ARCHIVE} && \
    unzip /tmp/tf012.zip -d /bin/
RUN curl -o /tmp/tf012-azurerm.zip ${AZURERM_ARCHIVE} && \
    unzip /tmp/tf012-azurerm.zip -d /bin
RUN curl -o /tmp/tf012-random.zip ${RANDOM_ARCHIVE} && \
    unzip /tmp/tf012-random.zip -d /bin
RUN curl -o /tmp/tf012-template.zip ${TEMPLATE_ARCHIVE} && \
    unzip /tmp/tf012-template.zip -d /bin

WORKDIR /terraform
ENTRYPOINT ["/bin/terraform"]