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