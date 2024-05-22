FROM node:21.7.3-alpine3.19

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

# Bundle app source
COPY . .

EXPOSE 3000
CMD ["yarn", "start"]