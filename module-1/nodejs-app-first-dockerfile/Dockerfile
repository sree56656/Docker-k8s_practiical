FROM node

WORKDIR /app

COPY package.json /app

RUN npm install
# even though if source code changes above steps will not run
COPY . /app 

EXPOSE 80

CMD ["node", "server.js"]