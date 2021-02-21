# Basic sample

using docker-compose.yml file to start 

```sh
docker-compose up -d
``` 

## setup plantuml rendering

* copy source from [github project plantuml-code-highlight](https://gitea.com/davidsvantesson/plantuml-code-highlight)
* place js files into a gitea/public folder under mountpoint /data 
* create a footer.tmpl in gitea/templates/custom/footer.tmpl

```
<script src="https://git.wils.tk/deflate.js"></script>
<script src="https://git.wils.tk/encode.js"></script>
<script src="https://git.wils.tk/plantuml_codeblock_parse.js"></script>
<script>
parsePlantumlCodeBlocks("https://puml.wils.tk")
</script>
``` 