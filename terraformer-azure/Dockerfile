FROM alpine:latest
LABEL maintainer marko

ARG TERRAFORM_VERSION

RUN apk add wget unzip curl git bash 

## Terraform
RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -P /tmp
RUN unzip /tmp/terraform*.zip -d /usr/bin/ && rm -f /tmp/terraform*.zip

## Azure cli
# RUN apk add --virtual=build gcc libffi-dev musl-dev openssl-dev python3-dev py3-pip py3-pynacl rpm
# RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
# COPY azure-cli.repo /etc/yum.repos.d/azure-cli.repo
# RUN pip3 install azure-cli

