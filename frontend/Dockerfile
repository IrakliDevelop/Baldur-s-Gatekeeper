FROM node:21.7.3-alpine3.19 as builder

# build "@baldurs-gatekeeper/common" package
WORKDIR /app
COPY package.json .
COPY yarn.lock .
COPY tsconfig.json .
COPY common ./common

WORKDIR /app/common
RUN yarn install
RUN yarn build

# Build the frontend
WORKDIR /app
COPY frontend ./frontend
WORKDIR /app/frontend
RUN yarn install
RUN yarn build

FROM nginx:alpine
COPY --from=builder /app/frontend/dist/frontend /usr/share/nginx/html
EXPOSE 80
