# Traefik 

## Quick start

```yml
version: '3'

services:
  reverse-proxy:
    # The official v2 Traefik docker image
    image: traefik:v2.2
    # Enables the web UI and tells Traefik to listen to docker
    command: --api.insecure=true --providers.docker
    ports:
      # The HTTP port
      - "80:80"
      # The HTTPS port
      - "443:443"
      # The Web UI (enabled by --api.insecure=true)
      - "8080:8080"
```

- starting traefik

```bash
docker-compose up -d reverse-proxy
```

- adding simple http service whoami to docker-compose file

```yml
  whoami:
    # A container that exposes an API to show its IP address
    image: containous/whoami
    networks:
      - web
    labels:
      - "traefik.http.routers.whoami.rule=Path(`/whoami`)"
```

- starting whoami 
```bash
docker-compose -d up whoami
```

- starting two instances of service whoami

```bash
docker-compose -d --scale whoami=2
```

- access via http://localhost/whoami

## file configuration provider

- addtional configuration as volume definition in docker-compose.yml

```yml
    volumes:
      # So that Traefik can listen to the Docker events
      - /var/run/docker.sock:/var/run/docker.sock
      - ./traefik.yml:/etc/traefik/traefik.yml
      - ./run/conf:/traefik/conf
      - ./run/ssl:/traefik/ssl
      - ./run/logs:/traefik/logs
```

## including tsl config

Infos:

- [Using HTTPS certificates with Traefik and Docker for a development environment](https://www.andrewdixon.co.uk/2020/03/14/using-https-certificates-with-traefik-and-docker-for-a-development-environment/)
- generating key, previously fill config file 

```bash
openssl req -new -sha256 -nodes -out traefik.csr -newkey rsa:2048 -keyout traefik.key -config traefik.ext
```
    
- signing csr and generating crt

```bash
openssl x509 -req -in traefik.csr -CA ~/myCA/myCA.pem -CAkey ~/myCA/myCA.key -CAcreateserial -out traefik.crt -days 365 -sha256
```

- generating extra (importand!) file to include tls configuration eg default-cert.yml
```yml
tls:
  stores:
    default:
      defaultCertificate:
        certFile: /traefik/ssl/traefik.crt
        keyFile: /traefik/ssl/traefik.key
  certificates:
    - certFile: /traefik/ssl/traefik.crt
      keyFile: /traefik/ssl/traefik.key
```