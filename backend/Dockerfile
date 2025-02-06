
FROM node:21 AS backend-builder

WORKDIR /app

COPY . .

RUN npm i

RUN npm run test

# Stage 2
FROM node:21-slim

WORKDIR /app

COPY --from=backend-builder /app .

COPY .env.docker .env

# Port
EXPOSE 5000

CMD ["npm", "start"]
