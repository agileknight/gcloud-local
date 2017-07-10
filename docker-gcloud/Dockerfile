FROM ubuntu:16.04

RUN apt-get update && apt-get install -y \
    curl \
    lsb-release \
    unzip \
    apt-transport-https \
    vim \
 && rm -rf /var/lib/apt/lists/*

# install google cloud SDK
RUN CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" \
  && echo "deb https://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
  && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
  && apt-get update && apt-get install -y \
    google-cloud-sdk \
    kubectl \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN curl -sSL -O https://get.docker.com/builds/Linux/x86_64/docker-1.11.2.tgz && tar xf docker-1.11.2.tgz && mv docker/docker /usr/local/bin && chmod a+x /usr/local/bin/docker && rm -rf docker* 
ENV PATH /usr/local/bin:$PATH

ENV TERRAFORM_VERSION 0.7.5
RUN mkdir /tmp/terraform \
    && cd /tmp/terraform \
    && curl -O -sS -L https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip \
    && unzip terraform_${TERRAFORM_VERSION}_linux_amd64.zip \
    && mv terraform /usr/local/bin \
    && rm -rf /tmp/terraform

# install rundeck ansible plugin and gce dynamic inventory script requirements
RUN apt-get update && apt-get install -y \
    ansible \
    python-libcloud \
    python-setuptools \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN easy_install pip

RUN apt-get update && apt-get install -y \
    build-essential \
    libssl-dev \
    libffi-dev \
    python-dev \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade cryptography
RUN pip install --upgrade ansible
RUN pip install --upgrade apache-libcloud
