ARG NODE_IMAGE
ARG PROJECT_ROOT

FROM node:${NODE_IMAGE}

WORKDIR ${PROJECT_ROOT}

RUN apk update && \
    apk add bash vim && \
    npm install -g npm && \
    npm install -g @nestjs/cli