FROM node:16.18

ENV PORT=3000

COPY . /client
WORKDIR /client
RUN npm install
EXPOSE 3000
CMD ["npm", "start"]