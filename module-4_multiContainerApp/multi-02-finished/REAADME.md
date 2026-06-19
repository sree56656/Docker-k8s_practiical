$ docker run -d -p 27017:27017 --rm --name mongodb mongo - mongo
$ docker run -p 80:80 -d --rm --name goals-backend goals-node - backend
$ docker run -p 3000:3000 -it --rm --name goals-react goals-react - frontend

React code runs on the browser not on the container, for frontend no need to add --network

$ docker run -p 80:80 --network goals-net --rm --name goals-backend goals-node  
$ docker run -d -v data:/data/db -p 27017:27017 --network goals-net --rm --name mongodb mongo - mongo

ENV MONGODB_USERNAME=root
$ docker run -d -v data:/data/db -p 27017:27017 -e MONGODB_USERNAME=sree -e MONGODB_PASSWORD=secret --network goals-net --rm --name mongodb mongo

==================================

$ docker run -p 80:80 --network goals-net --rm --name goals-backend -v  D:\Interview-codes\Docker-k8s-udemy\module-4_multiContainerApp\multi-01-starting-setup\backend:/app -v /app/node_modules -v logs:/app/logs goals-node  



=============== 
Final Commands

Frontend:
    $ docker build -t goals-react .
    $ docker run -v D:\Interview-codes\Docker-k8s-udemy\module-4_multiContainerApp\multi-02-finished\frontend\src:/app/src --name goals-frontend --network goals-net --rm -d --rm -p 3000:3000 -it goals-react

backend:
    $ docker build -t goals-backend .
    $ docker run -d -p 80:80 --network goals-net --rm --name goals-backend -v D:\Interview-codes\Docker-k8s-udemy\module-4_multiContainerApp\multi-02-finished\backend:/app -v /app/node_modules -v logs:/app/logs -e MONGODB_USERNAME=max  goals-backend 

MongoDB:
    $ docker run --name mongodb -v data:/data/db --rm -d --network goals-net -e MONGO_INITDB_ROOT_USERNAME=max -e MONGO_INITDB_ROOT_PASSWORD=secret mongo