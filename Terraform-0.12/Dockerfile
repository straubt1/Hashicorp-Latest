FROM alpine
ARG XC_OS="linux"
ARG XC_ARCH="386"
ARG TERRAFORM_VERSION="0.12.0-alpha4"
ARG TERRAFORM_ARCHIVE="https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_${XC_OS}_${XC_ARCH}.zip"

RUN apk add --update bash openssh zip curl && \
    mkdir '/terraform'
RUN curl -o /tmp/tf012.zip ${TERRAFORM_ARCHIVE} && \
    unzip /tmp/tf012.zip -d /bin/

WORKDIR /terraform
ENTRYPOINT ["/bin/terraform"]
