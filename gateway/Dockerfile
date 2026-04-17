FROM node:22-alpine

WORKDIR /app

COPY package.json package-lock.json ./
RUN npm ci --omit=dev

COPY src ./src

ENV GATEWAY_PORT=8000 \
    STAT_URL=http://stat:8002 \
    NLP_URL=http://nlp:8001 \
    JWT_SECRET=supersecret \
    DEMO_USER=admin \
    DEMO_PASS=admin123

EXPOSE 8000

CMD ["npm", "start"]
