FROM node:14-alpine 
ENV NODE_ENV production

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY . /usr/src/app/
RUN npm install


RUN npm install && npm install nodemon --save-dev

EXPOSE 5000
CMD ["yarn", "start"]
