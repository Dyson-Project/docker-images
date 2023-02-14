# ELK stack from scratch, with Docker

## Modify max virtual memory areas vm.max_map_count

Insert the new entry into the /etc/sysctl.conf file with the required parameter:

```
vm.max_map_count = 262144
```

Then `systemctl restart docker`

## Run (stack)

```
  # run (daemon)
  docker-compose up -d
  # show logs
  docker-compose logs -f
```

## Index management with curator

```
  docker run --network dockerelkstack_logging --link elastic:elasticsearch -v "$PWD/curator/config":/config --rm bobrik/curator:4.0.4 --config /config/config.yml /config/actions.yml
```
