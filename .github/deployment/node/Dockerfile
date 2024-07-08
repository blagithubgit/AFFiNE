FROM node:20-bookworm-slim

COPY ./packages/backend/server /app
COPY ./packages/frontend/web/dist /app/static
COPY ./packages/frontend/admin/dist /app/static/admin
WORKDIR /app

RUN apt-get update && \
  apt-get install -y --no-install-recommends openssl && \
  rm -rf /var/lib/apt/lists/* && npx prisma migrate status || true

CMD ["node", "--import", "./scripts/register.js", "./dist/index.js"]
