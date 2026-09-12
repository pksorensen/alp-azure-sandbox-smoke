FROM ghcr.io/pksorensen/pks-fullstack-base:latest

USER root

ARG NODE_VERSION=22.14.0
ARG NODE_SHA256=69b09dba5c8dcb05c4e4273a4340db1005abeafe3927efda2bc5b249e80437ec
ARG CODEX_VERSION=0.144.1
RUN curl -kfsSL -o /tmp/node.tar.xz \
      "https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.xz" \
    && echo "${NODE_SHA256}  /tmp/node.tar.xz" | sha256sum -c - \
    && tar -xJf /tmp/node.tar.xz -C /usr/local --strip-components=1 \
    && rm /tmp/node.tar.xz \
    && npm install -g "@openai/codex@${CODEX_VERSION}" \
    && node --version \
    && npm --version \
    && codex --version

USER node
