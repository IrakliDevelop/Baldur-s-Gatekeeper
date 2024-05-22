FROM node:21.7.3-alpine3.19 as builder

# build "@baldurs-gatekeeper/common" package
WORKDIR /app/common
COPY common/package.json ./
COPY common/yarn.lock ./
RUN yarn install
COPY common ./
RUN yarn build

WORKDIR /app
COPY package.json ./
COPY yarn.lock ./
RUN yarn install
COPY . .
RUN yarn build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
