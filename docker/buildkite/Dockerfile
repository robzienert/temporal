FROM golang:1.15

# Tried to set Python to ignore warnings due to the instructions at this link:
# https://github.com/yaml/pyyaml/wiki/PyYAML-yaml.load(input)-Deprecation
# But this causes all the pip installs to fail, so don't do this:
# ENV PYTHONWARNINGS=ignore::yaml.YAMLLoadWarning
# ENV PYTHONWARNINGS=ignore

RUN apt-get update && apt-get install -y --no-install-recommends \
      curl \
      gettext-base \
      libyaml-dev \
      python \
      python-dev \
      python-pip \
      python-setuptools \
      time \
      protobuf-compiler \
      && rm -rf /var/lib/apt/lists/* \
      && curl https://bootstrap.pypa.io/get-pip.py | python \
      && pip install PyYAML==3.13 \
      && go get -u github.com/axw/gocov/gocov \
      && go get -u github.com/mattn/goveralls \
      && go get -u golang.org/x/tools/cmd/cover \
# https://github.com/docker-library/golang/blob/c1baf037d71331eb0b8d4c70cff4c29cf124c5e0/1.4/Dockerfile
      && mkdir -p /temporal

WORKDIR /temporal
