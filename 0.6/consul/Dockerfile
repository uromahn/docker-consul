FROM ubuntu:14.04

ENV CONSUL_VERSION 0.6.5
ENV CONSUL_SHA256 

RUN apt-get update && apt-get install -y --no-install-recommends \
		ca-certificates \
		wget \
		zip \
		unzip \
	&& rm -rf /var/lib/apt/lists/*

ADD https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip /tmp/consul.zip

RUN echo "${CONSUL_SHA256}  /tmp/consul.zip" > /tmp/consul.sha256 \
  && sha256sum -c /tmp/consul.sha256 \
  && cd /bin \
  && unzip /tmp/consul.zip \
  && chmod +x /bin/consul \
  && rm /tmp/consul.zip

ENTRYPOINT ["/bin/consul"]
