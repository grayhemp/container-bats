ARG REGISTRY_NAMESPACE
ARG REGISTRY_TAG
FROM ${REGISTRY_NAMESPACE}/base:${REGISTRY_TAG}

RUN set -x \
  && url='https://github.com/bats-core/bats-core/archive/v1.1.0.tar.gz' \
  && sha256='855d8b8bed466bc505e61123d12885500ef6fcdb317ace1b668087364717ea82' \
  && mkdir -p ~/bats && cd ~/bats \
  && wget -nv -O bats.tar.gz "${url}" \
  && echo "${sha256}  bats.tar.gz" | sha256sum -c - \
  && tar --strip-components 1 -xf bats.tar.gz \
  && ./install.sh /usr/local \
  && cd ~ && rm -r ~/bats
