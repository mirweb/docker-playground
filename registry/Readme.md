# Local pass through docker registry

* inpired by [docker-local-cache](https://github.com/techmaniack/docker-local-cache)
* to use local cache in docker daemon.json
```
  "registry-mirrors": ["http://127.0.0.1:5000"],
```
* restart dockerd 
* to test cache
```bash
[0] % curl localhost:5000/v2/_catalog
{"repositories":[]}

[0] % docker info                    
Client:
 Context:    default
 Debug Mode: false
....
 Insecure Registries:
  127.0.0.0/8
 Registry Mirrors:
  http://127.0.0.1:5000/
 Live Restore Enabled: false

 [0] % docker rmi alpine
Untagged: alpine:latest

[0] % docker pull alpine             
Using default tag: latest
Status: Downloaded newer image for alpine:latest
docker.io/library/alpine:latest

[0] % curl localhost:5000/v2/_catalog
{"repositories":["library/alpine"]}

```