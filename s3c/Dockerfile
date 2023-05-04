
ARG FINAL_BASE=cgr.dev/chainguard/alpine-base

# BUILD
FROM $FINAL_BASE
WORKDIR /

# packages
RUN echo -e "\nhttp://dl-cdn.alpinelinux.org/alpine/v3.18/community" >> /etc/apk/repositories
RUN apk add --update bash curl jq cosign

# anchore tools 
RUN curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh \
    | sh -s -- -b /usr/local/bin

RUN curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh \
    | sh -s -- -b /usr/local/bin

# aquasecurity
RUN curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh \
    | sh -s -- -b /usr/local/bin

# cleanup
RUN rm -rf /var/cache/apk/*
