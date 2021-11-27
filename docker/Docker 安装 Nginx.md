# Docker 安装 Nginx

## 1.设置外部文件夹

随便启动一个 nginx 实例，只是为了复制出配置 

```shell
docker run -p 80:80 --name nginx -d nginx:1.10 
```

将容器内的配置文件拷贝到当前目录：

```shell
docker container cp nginx:/etc/nginx .
```

Note: 别忘了后面的点

修改文件名称：`mv nginx conf`把这个 conf 移动到 `/mydata/nginx` 下

终止原容器：

```she
docker stop nginx
```

执行命令删除原容器：

```shell
docker rm 容器ID
```



## 2.创建新的 Nginx 

```shell
docker run -p 80:80 --name nginx \
-v /mydata/nginx/html:/usr/share/nginx/html \
-v /mydata/nginx/logs:/var/log/nginx \
-v /mydata/nginx/conf:/etc/nginx \
-d nginx:1.10
```

