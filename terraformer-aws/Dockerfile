FROM ubuntu:latest
LABEL maintainer marko

ARG TERRAFORM_VERSION

RUN apt-get update && apt-get -y install wget unzip curl git

RUN wget https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -P /tmp

RUN unzip /tmp/terraform*.zip -d /usr/bin/ && rm -f /tmp/terraform*.zip

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "/tmp/awscliv2.zip" 
RUN unzip /tmp/awscliv2.zip 
RUN ./aws/install

RUN aws --version

VOLUME /local-git

RUN useradd -ms /bin/bash terraform

# USER terraform
WORKDIR /local-git