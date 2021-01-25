# Devops Pipeline

## Information

Common devops pipeline with 
* [gitea](https://gitea.com) as git repository
* [jenkins](https://www.jenkins.io) as build server
* [apache httpd](https://httpd.apache.org) as reverse proxy
* [Nexus Doc](https://help.sonatype.com/repomanager3) as maven repo and docker registry

## Running & Maintaining

* For starting services 

```bash
docker-compose up -d
```

* Following standard logs

```bash
docker-compose logs -f {service eg gitea}
```

* connecting to standard shell in container

```bash
docker-compose exec {service} bash
```

## Maintaing gitea

### Changing settings in app.ini

* attach to running container, go to conf folder, open app.ini
```
[0] %docker-compose exec gitea bash
bash-5.0# cd /data/gitea/conf/
bash-5.0# vi app.ini 
```
* change for example ROOT_URL

## Maintaining jenkins

* initial password can be find in logs at first start
* or at /var/jenkins_home/secrets/initialAdminPassword in startet container
* Dockerfile for setup /var/run/docker.sock taken from [github repo](https://github.com/jareddlc/jenkins-with-docker-socket/blob/master/lts/Dockerfile)

## Maintaining nexus 

* start password is under /nexus-data/admin.password