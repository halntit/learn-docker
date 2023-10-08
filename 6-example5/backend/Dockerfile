FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 8000

ENV MONGODB_USERNAME=admin
ENV MONGODB_PASSWORD=5ecr3t

CMD ["npm", "start"]
