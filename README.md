# my-docker
我的镜像

## 部署
### golang环境

```
docker run --name my-go-code-server -p 8090:8080 -v /my-project:/project -v /my-code-servere:/code-server/data -e PASSWORD=my-password -it -d mmyj/go-code-server
```
