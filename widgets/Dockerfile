FROM node:12.16.3-slim

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y \
    git nano && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /erxes

COPY --chown=node:node . /erxes

RUN yarn

RUN yarn build

RUN yarn global add serve

RUN chown -R node:node /erxes

USER node

EXPOSE 3200

ENTRYPOINT [ "node", "--max_old_space_size=8192", "dist" ]