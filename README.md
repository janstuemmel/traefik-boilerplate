# Proxy for docker containers

## Install

```sh
# edit email for letsencrypt in traefik.toml
nano traefik.toml

# edit hostname in docker-compose.yml
nano docker-compose.yml

# start proxy service + portainer
docker-compose up -d
```

## Add service

To add a service under a specific domain, set labels and network. You can eather set labels directly in the docker shell command or via a `docker-compose.yml` file.

Example:

```yml
version: '3'

networks:
  web:
    external: true

services:
  image: foo/bar
  networks: 
    - web
  labels:
    # set the hostname
    - traefik.frontend.rule=Host:foo.example.com
    # set a port if not 80 internally
    - traefik.port=8080
```

## Resources

* [Digital Ocean Tutorial on Traefik](https://www.digitalocean.com/community/tutorials/how-to-use-traefik-as-a-reverse-proxy-for-docker-containers-on-ubuntu-18-04)