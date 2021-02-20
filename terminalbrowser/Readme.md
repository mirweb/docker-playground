# simple docker images with installed termial browser

* see [You can Surf Internet in Linux Terminal With These Command Line Browsers](https://itsfoss.com/terminal-web-browsers/)

## build an run

```bash
[0] % docker build . -t terminalbrowser
[0] % docker run -it --rm terminalbrowser
root@d1cb4dee1f29:/#
```

## build and push to a docker regestry

```bash

[0] % docker build . -t regestry:5000/terminalbrowser:latest
[0] % docker login regestry:5000
[0] % docker push regestry:5000/terminalbrowser:latest   
```