FROM node:22-bookworm-slim

WORKDIR /app

RUN apt-get update \
  && apt-get install -y --no-install-recommends python3 make g++ \
  && rm -rf /var/lib/apt/lists/*

COPY server/package.json ./package.json
RUN yarn install --production --frozen-lockfile || yarn install --production

COPY server/src ./src
COPY server/tsconfig.json ./tsconfig.json

ENV CERU_SYNC_HOST=0.0.0.0
ENV CERU_SYNC_PORT=31231
ENV CERU_SYNC_DB_PATH=/data/ceru-sync.sqlite

VOLUME ["/data"]
EXPOSE 31231

CMD ["yarn", "start"]
