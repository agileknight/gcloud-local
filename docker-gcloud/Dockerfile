FROM google/cloud-sdk

RUN apt-get update && apt-get install -y \
    curl \
 && rm -rf /var/lib/apt/lists/*

RUN curl -sSL -O https://get.docker.com/builds/Linux/x86_64/docker-1.11.2.tgz && tar xf docker-1.11.2.tgz && mv docker/docker /usr/local/bin && chmod a+x /usr/local/bin/docker && rm -rf docker* 
ENV PATH /usr/local/bin:$PATH