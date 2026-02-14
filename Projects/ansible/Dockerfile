FROM node:16-alpine AS builder

WORKDIR /2048-game

COPY . .
RUN npm install --include=dev

RUN npm run build


FROM nginx:stable-alpine 
COPY --from=builder /2048-game/dist /usr/share/nginx/html
