FROM registry.access.redhat.com/ubi9/ubi:latest
ARG ORG_ID
ARG KEY_NAME

RUN set -eu
RUN echo "${ORG_ID}"
RUN echo "${KEY_NAME}"
RUN subscription-manager register --org="${ORG_ID}" --activationkey="${KEY_NAME}"
RUN dnf module enable -y nodejs:20
RUN dnf install -y nodejs
RUN subscription-manager unregister
RUN dnf clean all
