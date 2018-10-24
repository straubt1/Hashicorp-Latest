FROM alpine
ARG TERRAFORM_LOCATION="https://releases.hashicorp.com/terraform/0.12.0-alpha1/terraform_0.12.0-alpha1_linux_386.zip"

RUN apk add --update bash openssh zip curl && \
    mkdir '/terraform'
RUN curl -o /tmp/tf012.zip ${TERRAFORM_LOCATION} && \
    unzip /tmptf012.zip -d /bin/ && \
    mkdir '/terraform'

WORKDIR /terraform
ENTRYPOINT ["/bin/terraform"]