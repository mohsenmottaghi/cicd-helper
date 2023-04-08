FROM google/cloud-sdk:alpine
ENV HELM_VERSION "v3.10.3"
ENV YQ_VERSION "v4.30.5"
ENV VAULT_VERSION "1.12.2"

RUN apk add --no-cache curl wget openssl unzip >/dev/null 2>&1

RUN wget https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz 2>/dev/null && \
    tar xzf helm-${HELM_VERSION}-linux-amd64.tar.gz && mv linux-amd64/helm /usr/local/bin/ && \
    chmod +x /usr/local/bin/helm && rm -rf ./helm-${HELM_VERSION}-linux-amd64.tar.gz
RUN wget https://github.com/mikefarah/yq/releases/download/${YQ_VERSION}/yq_linux_amd64 -O /usr/local/bin/yq 2>/dev/null && \
    chmod +x /usr/local/bin/yq
RUN wget https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_amd64.zip 2>/dev/null && \
    unzip vault_${VAULT_VERSION}_linux_amd64.zip && mv ./vault /usr/local/bin && \
    chmod +x /usr/local/bin/vault && rm -rf ./vault_${VAULT_VERSION}_linux_amd64.zip

RUN gcloud components install kubectl gke-gcloud-auth-plugin --quiet
