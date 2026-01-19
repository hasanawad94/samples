FROM registry.access.redhat.com/ubi9/ubi:latest
ARG ORG_ID=""
ARG KEY_NAME=""

RUN set -eu; \
    ORG_ID_FILE=/etc/pki/entitlement/ORG_ID; \
    KEY_FILE=/etc/pki/entitlement/KEY_NAME; \
    ORG_ID_VAL="${ORG_ID}"; \
    KEY_VAL="${KEY_NAME}"; \
    if [ -f "$ORG_ID_FILE" ]; then ORG_ID_VAL="$(echo -n "$( < "$ORG_ID_FILE" )")"; fi; \
    if [ -f "$KEY_FILE" ]; then KEY_VAL="$(echo -n "$( < "$KEY_FILE" )")"; fi; \
    [ -n "$ORG_ID_VAL" ] && [ -n "$KEY_VAL" ]; \
    subscription-manager register --org="${ORG_ID_VAL}" --activationkey="${KEY_VAL}" && \
    dnf module enable -y nodejs:20 && \
    dnf install -y nodejs && \
    subscription-manager unregister && \
    dnf clean all
