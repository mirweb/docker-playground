# code-server sample

## infos

* [Docu about code-server](https://coder.com/docs/code-server/latest/guide)
* [linuxserver.io base image docu](https://docs.linuxserver.io/images/docker-code-server)

## addons

* add docker mods

```
    environment:
      - DOCKER_MODS=linuxserver/mods:code-server-docker|linuxserver/mods:code-server-java11|linuxserver/mods:code-server-zsh
```