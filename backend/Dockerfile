FROM node:21.7.3-alpine3.19

# build "@baldurs-gatekeeper/common" package
WORKDIR /app
COPY package.json .
COPY yarn.lock .
COPY tsconfig.json .
COPY common ./common

WORKDIR /app/common
RUN yarn install
RUN yarn build

WORKDIR /app/backend
COPY backend/package.json .
COPY backend/yarn.lock .
RUN yarn install

COPY backend .
RUN yarn build

CMD ["yarn", "start"]