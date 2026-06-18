1. Container to WWW web just works fine without any extra settings

2. Container to host machine connection
    $ host.docker.internal instead of localhost
    mongodb://host.docker.internal:27017/swfavorites', 

3. container to container
    a. we had to look at IP address of other container and call it
        mongodb://172.17.0.2:27017/swfavorites',
    b. docker run --network my_network
        if containers are in same network they can talk to each other
        $ docker network create favorites-net
        $ docker run -d --rm -p 3000:3000 --network favorites-net --name favorites favorites-node
        $ docker run -d --network favorites-net --name mongodb mongo
        mongodb://<container name>:27017/swfavorites',