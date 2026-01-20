FROM registry.access.redhat.com/ubi9/ubi:latest
ARG ORG_ID
ARG KEY_NAME

RUN set -eu; \
    subscription-manager register --org="$(cat /etc/pki/entitlement/ORG_ID)" --activationkey="$(cat /etc/pki/entitlement/KEY_NAME)" && \
    dnf module enable -y nodejs:20 && \
    dnf install -y nodejs && \
    subscription-manager unregister && \
    dnf clean all
