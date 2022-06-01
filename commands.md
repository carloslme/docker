#### Check containers information
```
docker ps -a
```

#### Check memory usage
```
docker stats
```

#### Restrict memory usage in yml file
Go to the container and add the entry as follows

```
your_project:
    deploy:
        resources:
            limits:
                cpus: "0.15" # this is the % of total memory
                memory: 250M
            # dedicated resources, keep them as minimal as possible
            reservations:
                cpus: 0.1
                memory: 128M
```

Then stop the containers, and recreate them.

```
docker-compose -f stack-billing.yml stop

docker-compose -f stack-billing.yml up -d --force-recreate
```

#### Delete images
```
docker images prune
```

#### Delete networks
```
docker network prune
```

#### Stop all containers
```
docker stop $(docker ps -a -q)
```

#### Delete all stopped containers
```
docker container prune
```

#### Create images
```
docker-compose -f stack-billing.yml build --no-cache
```