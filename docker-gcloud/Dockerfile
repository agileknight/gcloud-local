FROM google/cloud-sdk

RUN apt-get update && apt-get install -y \
    curl \
 && rm -rf /var/lib/apt/lists/*

RUN curl -sSL -O https://get.docker.com/builds/Linux/x86_64/docker-1.11.2.tgz && tar xf docker-1.11.2.tgz && mv docker/docker /usr/local/bin && chmod a+x /usr/local/bin/docker && rm -rf docker* 
ENV PATH /usr/local/bin:$PATH

ENV TERRAFORM_VERSION 0.7.5
RUN mkdir /tmp/terraform \
    && cd /tmp/terraform \
    && curl -O -sS -L https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip \
    && unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip \
    && mv terraform* /usr/local/bin \
    && rm -rf /tmp/terraform
