FROM node:latest
RUN npm install nodemon -g
WORKDIR /usr/src/app
ADD . /usr/src/app
RUN npm install
EXPOSE 8080
CMD ["npm", "start"] 
