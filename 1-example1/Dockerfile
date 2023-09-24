FROM node

WORKDIR /app

COPY package.json /app

RUN npm install

# when only code changed, no need to run npm install
COPY . /app

# optional (because this is the default), but recommended (best practice)
EXPOSE 80

CMD [ "node", "server.js" ]