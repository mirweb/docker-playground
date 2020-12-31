# Sonatype Nexus

* [Nexus Doc](https://help.sonatype.com/repomanager3) 
* [Nexus Docker Image Doc](https://hub.docker.com/r/sonatype/nexus3/)


## Basic usage

* go to http://localhost:8081
* start password is under /nexus-data/admin.password

## Docker hub 

* create docker repo at port 8082 for local use
* add "Docker Bearer Token Realm" under securtiy -> reals to active ([see](hhttps://help.sonatype.com/repomanager3/formats/docker-registry/docker-authentication))

```sh
docker pull hello-world
docker tag hello-world localhost:8082/hello-world
docker login localhost:8082
docker push localhost:8082/hello-world 
```


