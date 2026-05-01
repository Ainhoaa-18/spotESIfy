# SpotESIfy API — Dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN apk add --no-cache curl
RUN npm install --production

COPY server.js seed.js ./

USER node

EXPOSE 5000

HEALTHCHECK --interval=10s --timeout=3s --retries=3 \
  CMD curl -f http://localhost:5000/api/health || exit 1

CMD ["npm", "start"]
