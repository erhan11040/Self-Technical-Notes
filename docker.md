docker NOtes
Node example with ts

--commands--

docker build . -t <your username>/node-web-app //build current directory
docker run -p 8000:8000 -d <your username>/node-web-app

docker images //list images
docker ps //get processes
docker logs <contrainer id>//outputs of console

docker exec -it <container id> /bin/bash //enter inside the container
curl -i localhost:49160 //curl request to test if its working

docker save imagename --output imagename.tar  //export
docker load -i imagename.tar //import

docker stop containername
docker container rm cc3f2ff51cab //delete

docker image ls //list
docker image rm imagename //delete



--*dockerfile*-
FROM node:14-alpine
ENV NODE_ENV=production
WORKDIR /usr/src/app
COPY ["package.json", "package-lock.json*", "npm-shrinkwrap.json*", "./"]
RUN npm install --production --silent && mv node_modules ../
RUN npm build
COPY . .
EXPOSE 8080
CMD ["node", "build/index.js"]

--*packageJson*--
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "serve": "nodemon index.ts",
    "build": "tsc --project ./"
  },