FROM node:13
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
COPY set_env.sh .
## A wildcard is used to ensure both package.json AND package-lock.json are copied where available (npm@5+)
COPY package*.json ./
RUN npm install
RUN npm install dotenv
## Bundle app source
COPY . .
RUN chmod +x set_env.sh && ./set_env.sh
EXPOSE 8080
CMD [ "npm", "run", "dev" ]