### Build
FROM beevelop/ionic:latest AS ionic

## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./

RUN npm ci -f
## Bundle app source
COPY . .

# ENV NODE_TLS_REJECT_UNAUTHORIZED=0
# ENV NODE_OPTIONS=-openssl-legacy-provider

ENV NODE_OPTIONS="--openssl-legacy-provider"

RUN ionic build
### Run 
FROM nginx:alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html